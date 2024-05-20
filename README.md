class ToDoList:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append({"task": task, "completed": False})

    def delete_task(self, task):
        for t in self.tasks:
            if t["task"] == task:
                self.tasks.remove(t)
                return
        print("Task not found.")

    def mark_complete(self, task):
        for t in self.tasks:
            if t["task"] == task:
                t["completed"] = True
                return
        print("Task not found.")

    def view_tasks(self):
        if not self.tasks:
            print("No tasks in the list.")
            return
        for t in self.tasks:
            status = "Complete" if t["completed"] else "Incomplete"
            print(f"{t['task']} - {status}")

if __name__ == "__main__":
    todo_list = ToDoList()
    while True:
        print("\nTo-Do List Options:")
        print("1. Add Task")
        print("2. Delete Task")
        print("3. Mark Task as Complete")
        print("4. View Tasks")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            task = input("Enter the task: ")
            todo_list.add_task(task)
        elif choice == '2':
            task = input("Enter the task to delete: ")
            todo_list.delete_task(task)
        elif choice == '3':
            task = input("Enter the task to mark as complete: ")
            todo_list.mark_complete(task)
        elif choice == '4':
            todo_list.view_tasks()
        elif choice == '5':
            break
        else:
            print("Invalid choice. Please try again.")
