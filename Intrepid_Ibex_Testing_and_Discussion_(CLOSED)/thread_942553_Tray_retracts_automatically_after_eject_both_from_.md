---
title: "Tray retracts automatically after eject both from gui and terminal"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by RaZoR1394 on 2008-10-09
Hello

I'm having trouble ejecting my discs since updating yesterday. When I eject them from the gnome desktop, nautilus or the terminal the tray retracts just when the tray has finished ejecting. It doesn't matter if I have acutally used files on the disc it retracts anyway.

The only relevant part in dmesg was this:


```

[ 3778.241891] UDF-fs: Partition marked readonly; forcing readonly mount
[ 3778.323980] UDF-fs INFO UDF: Mounting volume '*DISC TITLE REMOVED*', timestamp 2008/10/09 15:12 (1078)

```

There is a difference when ejecting the disc at the login screen when noone's logged in. The retract doesn't happen until at least 10 seconds after a full eject so It's easier to remove the disc.

What could be causing this?

---

### Post by Muffe on 2008-10-10
I have the same problem as you... It's annoying to slip the CD out in a fraction of a second every time...

---

### Post by ViRMiN on 2008-10-10
Hmmm... mine stay open...

---

### Post by philinux on 2008-10-10
Mine retracts in the blink of an eye. If I then hit the eject button before it gets mounted it stays open.

---

### Post by shane19174 on 2008-10-10
Same thing here. I noticed it after burning a CD image with Brasero, and I've reproduced it twice. Where should we be posting this bug? Or is it already known?

Shane

---

### Post by philinux on 2008-10-10
Tried to report the bug and found it's already done.
[https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931](https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931)

---

### Post by RaZoR1394 on 2008-10-10
I guess I have to stay with 2.6.27-5 until this gets fixed because I use discs a lot. Problem is that there doesn't seem to be a working nVidia kernel module for that kernel on my system. I suspect it has something to do with the new DKMS building.

I'm reading the DKMS docs from Dell, trying to get a hang of it.

[http://linux.dell.com/dkms/dkms-ols2004.pdf](http://linux.dell.com/dkms/dkms-ols2004.pdf)

---

### Post by shane19174 on 2008-10-13
Are you guys keeping up with this bug? As I reported there ([https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931]("https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931")), it makes it impossible to copy a CD in Brasero, which seems like a pretty big deal (because such a basic function). Anyone have a workaround or know of progress on this?

---

### Post by RaZoR1394 on 2008-10-14
I have noticed i/o errors both when scanning and using the dvd burner. Maybe it has something to do with it? As I've said before 2.6.27-5 works for me but now I've removed that one because I wanted to reinstall it only to see that It's no longer available, so I'm stuck with 2.6.27-6 and -7. If you still have -5 try that one.

---

### Post by Sir Rodness on 2008-10-24
Guess I'm not alone. My trays retract too and stay open if I hit eject before it remounts. I'm about to check out the thread that was posted earlier to see what I can find.

---

### Post by Polygon on 2008-10-24
> **philinux said:**
> Mine retracts in the blink of an eye. If I then hit the eject button before it gets mounted it stays open.

same here

---

### Post by shane19174 on 2008-10-24
As noted elsewhere, here's the bug: [https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931]("https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931"). I suppose everyone facing this issue (is anyone not?) should add themselves. But maybe someone more experienced with the triaging process could point out if we need to be adding any particular logs or other output to that bug, as its status is still "undecided".

---

### Post by kansasnoob on 2008-10-24
Keep adding comments to the bug report!

I first encountered this testing the Beta ISO and reported it then!

I also find it almost unbelievable that it's importance is undecided:confused:

We need to hammer this home!

---

### Post by Podex on 2008-10-24
No developer has been assigned to this bug? This should definitely be a showstopper for Intrepid.

---

### Post by kansasnoob on 2008-10-24
It sure makes creating backups to a DVD+RW interesting:mad:

---

### Post by cor2y on 2008-10-24
Yes brasero can't verify backups right away it always gives an error you have to verify after the error and by ejecting the diisc again so it can get mounted again.

---

### Post by kyleabaker on 2008-10-25
> **Sir Rodness said:**
> Guess I'm not alone. My trays retract too and stay open if I hit eject before it remounts. I'm about to check out the thread that was posted earlier to see what I can find.

Same problem here as well.

---

### Post by ciscosurfer on 2008-10-25
> **philinux said:**
> Mine retracts in the blink of an eye. If I then hit the eject button before it gets mounted it stays open.Same thing here.  I'm running the RC.  I completely agree that this is a major problem.  If it was seen in alpha, this bug should've been squashed in beta, let alone the RC.  Truly disconcerting at 6 days to final release [-X

---

### Post by pulpo69 on 2008-10-25
here the dvd-drive problem too.

---

### Post by pulpo69 on 2008-10-25
i don't know but maybe it has something to do with the fstab line of the drive? here is my line: 
/dev/scd0       /media/cdrom0   auto   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by ronnielsen1 on 2008-10-25
> This should definitely be a showstopper for Intrepid.
It's not just Intrepid. I've noticed the problem in Mepis 7 & 8, and a couple of other distros. Anytime I have to change cd's I get it already first and then quickly change them. It is annoying.

---

### Post by ajackson on 2008-10-25
You wouldn't think that the code to eject CDs would need to change so the problem probably lies elsewhere.

In the meantime we all get to sharpen our reflexes up to ninja levels :)

---

### Post by kyleabaker on 2008-10-25
> **ajackson said:**
> ..we all get to sharpen our reflexes up to ninja levels :)
Not something I want to have to do constantly. ;)

---

### Post by Ellipsis on 2008-10-25
> **kyleabaker said:**
> Not something I want to have to do constantly. ;)

You wouldn't have to do it if you were already a ninja...

I am guessing there is no chance of getting this fixed before the final release?

---

### Post by sheldo on 2008-10-25
It is a bug in udev.  The fix mentioned here
[http://bugs.gentoo.org/show_bug.cgi?id=230886](http://bugs.gentoo.org/show_bug.cgi?id=230886)
and here
[https://bugzilla.redhat.com/show_bug.cgi?id=453095#c26](https://bugzilla.redhat.com/show_bug.cgi?id=453095#c26)
worked for me.

---

### Post by heavensblade23 on 2008-10-25
Also having this issue, but only if there is a disc in the tray already.

---

### Post by kansasnoob on 2008-10-25
> **sheldo said:**
> It is a bug in udev.  The fix mentioned here
[http://bugs.gentoo.org/show_bug.cgi?id=230886](http://bugs.gentoo.org/show_bug.cgi?id=230886)
and here
[https://bugzilla.redhat.com/show_bug.cgi?id=453095#c26](https://bugzilla.redhat.com/show_bug.cgi?id=453095#c26)
worked for me.

Awesome! That worked! What I did (per the bugzilla.redhat link):

I first ran the command:

```
cat /etc/udev/rules.d/60-persistent-storage.rules
```

I then used cut-n-paste to create a simple copy of the original directory just in case I hosed something. (There's probably a smarter way to create a backup of the original.)

I then ran the command:

```
sudo gedit /etc/udev/rules.d/60-persistent-storage.rules
```

Which opened the file in a text editor. Somewhat towards the bottom of the file you'll see the lines:

[B]# skip unpartitioned removable media devices from drivers which do not send "change" events
 ENV{DEVTYPE}=="disk", KERNEL!="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"

 
 # import filesystem metadata
 IMPORT{program}="vol_id --export $tempnode"[/B]

I then added the line:

**ENV{DEVTYPE}=="disk", KERNEL=="sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"**

As indicated here by the + mark (don't include the + mark in the edit):

[B]# skip unpartitioned removable media devices from drivers which do not send "change" events
 ENV{DEVTYPE}=="disk", KERNEL!="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"
+ENV{DEVTYPE}=="disk", KERNEL=="sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"
 
 # import filesystem metadata
 IMPORT{program}="vol_id --export $tempnode"[/B]


It looks better here:

[https://bugzilla.redhat.com/attachment.cgi?id=312742](https://bugzilla.redhat.com/attachment.cgi?id=312742)

When you're done editing you must click on Save and then File > Quit!

Hope this is clear as mud:confused:

---

### Post by Polygon on 2008-10-25
> **Ellipsis said:**
> You wouldn't have to do it if you were already a ninja...

I am guessing there is no chance of getting this fixed before the final release?

im pretty sure they will release an update that fixes it after intrepid gets releaesd

---

