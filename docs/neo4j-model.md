## Nodes:

- **User**: The User node would represent a Discord user, and it would contain the following properties:
    - `discordID`: The unique Discord ID of the user.

- **Chore**: The Chore node would represent a task to be done, and it would contain the following properties:
    - `description`: A brief description of the chore.
    - `creationDate`: The date when the chore was created or added to the system.
    - `frequency`: The frequency with which this chore needs to be done (daily, every three days, etc.).

## Relationships:

**CLAIMS**: A CLAIMS relationship would connect a User node to a Chore node, representing that the user has claimed responsibility for the chore. 

This relationship could have the following properties:

- `claimDate`: The date and time when the chore was claimed.
- `completeDate`: The date and time when the chore was marked as complete. If the chore hasn't been completed yet, this could be null.

Since multiple users can claim a chore, there can be multiple CLAIMS relationships to a single Chore node. When a user completes a chore, you can set the completeDate on their CLAIMS relationship to the current date and time.

## Queries:

As for queries, here are some examples of ones you might need:

- Get all chores that haven't been claimed yet: You can do this by looking for Chore nodes that don't have any CLAIMS relationships, or where all CLAIMS relationships have a non-null completeDate.

- Get all chores that a specific user has claimed but not completed: You can do this by looking for CLAIMS relationships from a given User node where completeDate is null.

- Get all chores that are due to be reminded: This might be a bit trickier, since it involves the chore's frequency and the time since it was last claimed or reminded. You might need to store some additional data on the Chore node or the CLAIMS relationships to support this query efficiently.

- Get all users who have claimed a particular chore: This can be done by traversing the CLAIMS relationships from a Chore node.