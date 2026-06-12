---
title: "Space error while updating"
date: 2022-01-19
forum: Installation &amp; Upgrades
---

### Post by pgte3 on 2022-01-19
Getting this error when updating:

"The upgrade needs a total of 409 M free space on disk '/boot'. Please free at least an additional 125 M of disk space on '/boot'. You can remove old kernels using 'sudo apt autoremove', and you could also set COMPRESS=xz in /etc/initramfs-tools/initramfs.conf to reduce the size of your initramfs."

I have tried both suggestions in error message, how do I clear this up?

---

### Post by Impavidus on 2022-01-19
Try adding the picture as an attachment. I can't see it when it's still on your computer.

---

### Post by pgte3 on 2022-01-19
I pasted the text from the error message.

---

### Post by Impavidus on 2022-01-19
Let's see this:```
df -h
dpkg --list 'linux-*' | grep -v '^rc'
```The first will show your filesystems and the free space on them, the second will show the installed kernel packages, but skip those with only config files.

---

### Post by pgte3 on 2022-01-19
Attached is the screenshot of error and what /boot looks like.

---

### Post by pgte3 on 2022-01-19
I ran those two commands:

/dev/sda5                  704M  382M  271M  59% /boot

Need to free up some space.

Not sure how to use the results of the second command to do some clean up? I see many "older" packages.

---

### Post by QIII on 2022-01-19
There should be much more to df -h than that.  Please copy and paste the results in their entirety.  /boot shouldn't be large and it should not be the issue here.  / is.

Please paste the text between code tags rather than posting images.  Images can deter those with slow connections or data limits from helping you.  They are also often difficult to read.

To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by Impavidus on 2022-01-19
It looks like the /boot partition is the issue here, although the screenshot is a bit hard to read. You have three kernels installed (normal is only two, as the third gets deleted right after a new kernel is installed. Further, it appears that you have some 5.15 kernels installed. Those aren't standard on any Ubuntu release. Can you tell us which version of Ubuntu you run? And why those 5.15 kernels are there?

---

### Post by ActionParsnip on 2022-01-19
What is the output of
```

dpkg -l | grep linux-image

```

---

### Post by QIII on 2022-01-19
Excellent!  My bad!

I'll just go clean my trifocals now.

---

### Post by pgte3 on 2022-01-20
Attached is a screenshot of the: dpkg -l | grep linux-image command.

I do not know why I have this many installed or how to clean them up.

---

### Post by pgte3 on 2022-01-20
I did some research and ran this command: sudo apt-get &#8211;&#8211;purge autoremove

This seems to have cleared up my space issue.

---

### Post by Impavidus on 2022-01-21
Copying the text to your forum post (in code tags) is easier than a screenshot.

All those kernels on lines starting with rc aren't really installed. They have been removed, but without removing configuration files, which can be removed when you purge the package. In fact, these kernel packages have no configuration files (other than some empty directories), so this purge will lead to little more than removal of clutter in the package manager.

You do have both the 5.13 kernel (from the official Ubuntu repos) and the 5.15 kernel (from somewhere else). Having additional kernels uses extra space in /boot. Normally autoremove just keeps one old kernel, but as you have metapackages pulling in two different kernel lines, you keep more.

Any particular reason for using the 5.15 kernel? And if you have, have you any particular reason for also keeping the 5.13 kernel?

---

### Post by ekhoollms on 2022-01-21
it clears my doubt

---

