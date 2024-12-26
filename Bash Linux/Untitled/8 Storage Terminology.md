
## Storage terminology

File space is the physical collection of storage devices combined to make up the locations of all files and directories.
the files and folders are `logical` view of the file space.

We can view the file space as devices, partitions, mountings and breakdown of the files into their disk block. This is the physical view of the file space.

Os have commands to show both the views but we prefer to see by the logical view.

`file` represents the smallest logical unit within the file space.
Files themselves are stored as a collection of disk blocks.
blocks of a single file are not necessarily stored `contiguously` on disk but instead scattered across one or more disk surfaces.
`file` have properties, like filename. (letters, numbers and `_` )

`directories` are a way to organize files. sub-directories create a hierarchical file space.

Linux has a pre-established set of directories referred to as `top-level directories`.

we will be in `current working directory`.
accessing files in another directory needs specifying a directory path.

`absolute path` always starts from the root directory.
`relative path` describes the change from where we are to where we want to go.

Directories are grouped together into partitions.
`partition` is the physical division of the collection of storage devices into independent units.

For backing up, we can unmount a specific partition containing that content and while unmounted, no one can access it. Other partitions will not be affected.

Logical volume manager(LVM) is an alternative to physical partitioning, it does not restrict any partition growth. But few disadvantages as a overhead to disk access. also the problem with loading the `kernel` files of Linux

Linux offers three separate partitions: `/boot`, `LVM` and `swap`
`/boot` must be separated from `LVM` and also `swap` as swap space (virtual memory) is treated differently from rest of the file space and not directly accessed by the user.

***inode***
`inode` is additional component of `Linux file space`
`inode` is a data structure which stores file information (meta-data) and pointers to the various file blocks on disk.
`inode` is dedicated to every file, directory and symbolic link in the file space.
the information it stores includes the file's type, owner, group, permissions and last access/create/modification date.

Another one is `link`,
`link` is a pointer which points from a file in a directory to its `inode` which contains pointers to point at the files's physical blocks.

There are two types of links, 
`hard link` points directly at the file's `inode`.
`soft link` or `symbolic link` points at a hard link.

For a symbolic link, the first character of a symbolic link, in the permission is `l`.
and the name is indicated as `link -> file` where `link` is the symbolic link and the `file` is the item being pointed at. The file will be in another directory.

The hard link's type is not `l` but it will be the type of the file being pointed to, that is `-` for a regular file and `d` for a directory.
The name is the `links` name and there is no `->` or separate `file` name.
The hard link count is greater than one.

When a file has a single pointer pointing to it, its hard link count is one.  
greater than one indicates more than one link to that item. all Directories have count of at least 2.


***The top level structure***
All distros contain a minimum `/boot` `/dev` `/etc` `/home` `/proc` `/var` and `/usr`.
Some directories will have pre-established internal structure.

[top-level directory structure of linux]
