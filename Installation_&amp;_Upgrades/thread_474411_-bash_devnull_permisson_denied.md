---
title: "-bash: /dev/null permisson denied"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by RadarListener on 2007-06-15
I am getting this message:
-bash: /dev/null permisson denied

spread over more than a screen's worth of lines when I put the CD in my CD drive and select the first option.

I checked the disk for defects and it comes up with errors. I can put the CD into two other computers and run the disk check on them and it works without a problem.

I have swapped the CD drives over from one of the working computers into the not-so-working computer, and I still get the same error.

I have also re-downloaded the ISO and burnt it at a slower speed. 

I've been on the problem all day and I'm at a loss at what could be causing it!

---

### Post by Mr. C. on 2007-06-15
Either the file /dev/null has been deleted or its permissions were changed.

/dev/null is the unix/linux bit-bucket, used generally for ignoring a program's output.

If the /dev/null file is removed, then scripts which attempt to redirect their output to /dev/null will in effect be attempting to create a new file in /dev, a directory where they will generally not have permission to write.

Please show the output of the terminal command:

```
ls -l /dev/null
```

MrC

---

### Post by RadarListener on 2007-06-15
MrC,

/dev/null's permissions are whatever the install CD sets them to. I do not have access to the computer over this weekend, but I'm sure that permissions could not be the problem.

This happens when I insert the disk and select the first option. It fails to start x also.

---

### Post by Mr. C. on 2007-06-15
Well, since you *know* what the problem isn't, I suppose there is not much I can help with.

I gave you the two primary possibilities that will cause your issue.  You can decide to follow through with running the command that will verify/exclude the theory.  Evidence is far stronger and more convincing than hearsay.

MrC

---

### Post by RadarListener on 2007-06-17
The output of the command ls -l /dev/null is:

crw-rw-rw- 1 root root 1, 3 2007-04-15 11:49 /dev/null

Why would it have the incorrect permissions on the install CD? The same install CD that I used to install it on two other computers fine?

---

### Post by Mr. C. on 2007-06-18
Ok, seeing permissions, there is something trying to execute /dev/null in a script.  This is likey caused by some variable that is unset.  For example:

```
$ /dev/null
bash: /dev/null: Permission denied

$ somevar=
$ $somevar /dev/null
bash: /dev/null: Permission denied
```

Now, you need to isolate which script is being called, and which variable is unset or has no value.

MrC

---

