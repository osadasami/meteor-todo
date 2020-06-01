<script>
  import { Meteor } from 'meteor/meteor'
	import { Tasks } from "../api/tasks.js"

	export let key
	export let task

	function toggleChecked() {
    Meteor.call('tasks.setChecked', task._id, !task.checked)
	}

	function deleteThisTask() {
    Meteor.call('tasks.remove', task._id)
	}
</script>
 
<li class:checked="{task.checked}">
  <button class="delete" on:click={deleteThisTask}>
    ×
  </button>
 
  <input
    type="checkbox"
    readonly
    checked={!!task.checked}    
    on:click={toggleChecked}
  />
 
  <span class="text">
    <strong>{task.username}</strong>
    : { task.text }
  </span>
</li>