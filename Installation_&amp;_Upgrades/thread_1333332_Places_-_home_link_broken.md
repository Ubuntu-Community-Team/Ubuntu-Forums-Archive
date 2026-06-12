---
title: "Places - home link broken"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by hangman_jdf on 2009-11-21
Did a clean install of 9.10.  I have my /home on a different partition.  When I try to open /home from places, F-spot tried to open and failed (probably a different issue with F-spot).  I removed F-spot and now I get an error: Could not open location 'file:///home/myusername'.  I am able to get to my /home through the filesystem or using terminal; it is through Places that I am unable.  I think that there is a broken link, but I am unable to find it.

I made sure I chose an application to open the folder, nautilus (file browser).

Any ideas?

---

### Post by drs305 on 2009-11-21
Is this what you tried? Right clicking on any folder in your file browser (Nautilus) and select "Open With", Other Application, and then File Browser?

---

### Post by hangman_jdf on 2009-11-21
Yes, and that works.

Only when I go from the Main Menu - Places - Home (or any other file connected to /home do I get the error).

Error:  "Failed to execute child process "f-spot-import" (No such file or directory)"

---

### Post by drs305 on 2009-11-21
You might try looking at ~/.local/share/applications/mimeapps.list to see if fspot is listed there or if nautius is registered.

Here is what my line looks like:
> inode/directory=nautilus-folder-handler.desktop;

A quick way to view it:
```

grep "inode" ~/.local/share/applications/mimeapps.list

```

A more aggressive remedy may be to rename .local to something else. A new .local folder will be regenerated when you log off and log back in.

---

### Post by hangman_jdf on 2009-11-21
Thanks.  I think that I fixed it.  The linking appears to work.  Not sure how the "f-spot-import.desktop" got there.

The file had this on the line:  
    inode/directory=f-spot-import.desktop;nautilus-folder-handler.desktop;nautilus.desktop;

Changed the line to read:
    inode/directory=nautilus-folder-handler.desktop;nautilus.desktop;

---

