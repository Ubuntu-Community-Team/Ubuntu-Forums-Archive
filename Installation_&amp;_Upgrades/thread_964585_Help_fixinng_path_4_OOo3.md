---
title: "Help fixinng path 4 OOo3"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by kennydidit on 2008-10-31
Hey after I upgraded to 8.10 OOo3 failed to open I got this error

Failed to execute child process "/usr/bin/oowriter" (No such file or directory)


dummy here did not save my old setting so now I know I have to redo the paths ,but I am not sure how to go about that? can anyone help?

---

### Post by cyfur01 on 2008-10-31
You'll have to add the file where the binaries are to your path, or else create links to the binaries in a folder that's already in your path.

To add a folder to your path, add this line to end end of your ~/.bashrc file:
```

export PATH=$PATH:path/to/folder:another/folder

```
Then either restart your terminal or else run:
```

source ~/.bashrc

```

To create a symbolic link in a folder that is already in your path:
```

sudo ln -s /install/path/program /folder/in/path/linkname

```

---

### Post by kennydidit on 2008-10-31
HEY cyfur01 sorry I did not get back to you last night. When I tried to do what you said permission  was denied in terminal mode when I tried to open supper user mode nothing happened, the menu went away but I got no window. I decided to try remove from synaptic  then reinstall Ooo3 which did work, but in the middle of all that I needed to get some sleep so I finished it this morning. I do thank you for your help

---

