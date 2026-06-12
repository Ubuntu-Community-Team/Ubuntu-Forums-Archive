---
title: "Using GRUB to boot from CDROM / Live cd"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by reformedgeek on 2008-01-02
Hi All,
I've checked a few posts on the forums.

The issue is I'm trying to reinstall Ubuntu on an old latitude which doesn't allow booting from CDROM.
Originally I used WUBI to force boot into the live cd then format/install.
Now however, having only 7.10 on the disk, I want to experiment with lighter distros and the Ubuntu Alt CD.
Any ideas how I can get GRUB to boot the LiveCD?
Is it simply a case of pointing it to the drive/kernel image? if so, what would the drive letter be? (hd0,0) is the hdd, so what does that make the CDrom?

please help :)

---

### Post by jken146 on 2008-01-02
I'm not sure how you would go about doing this.  If you can boot from USB take a look at pendrivelinux.com.

---

### Post by reformedgeek on 2008-01-02
Unfortunately not, 
It's a bit of a relic and doesnt support usb booting...

---

### Post by logos34 on 2008-01-02
try this:
[http://ubuntuforums.org/showthread.php?t=168693&highlight=sbm+syslinux+boot+cd](http://ubuntuforums.org/showthread.php?t=168693&highlight=sbm+syslinux+boot+cd)

---

### Post by reformedgeek on 2008-01-02
Aha, I saw this but wasn't sure. thanks! I'll try it

---

### Post by ~LoKe on 2008-01-02
You know, up until recently I've been having troubles getting my computer to boot from my CDRom.  It just wouldn't do it.  Now that I've actually got it to work, I find this post.  Grawr.

I'll bookmark it just in case.

---

### Post by reformedgeek on 2008-01-02
And it freakin' worked too!! Excellent stuff. :):):)

---

### Post by ~LoKe on 2008-01-02
> **reformedgeek said:**
> And it freakin' worked too!! Excellent stuff. :):):)

Good to know.  Hell, I'm just gonna add it in now in case I need it later and lose the guide.

---

### Post by logos34 on 2008-01-02
> **reformedgeek said:**
> And it freakin' worked too!! Excellent stuff. :):):)

Good to hear!  

Yeah, it's a lesser-known trick, seems to have been buried and forgotten in the dapper archives...I chanced upon it about nine months back, linked to it from the gentoo guide which I could never get to work properly.  Ever since then I've had it on my menu.lst--in my case it saves the hassle of having to change the Bios every time I want to boot from cdrom.

---

### Post by ~LoKe on 2008-01-02
> **logos34 said:**
> Good to hear!  

Yeah, it's a lesser-known trick, seems to have been buried and forgotten in the dapper archives...I chanced upon it about nine months back, linked to it from the gentoo guide which I could never get to work properly.  Ever since then I've had it on my menu.lst--in my case it saves the hassle of having to change the Bios every time I want to boot from cdrom.

One of the mods made a post in the cafe about something along the lines of "guide of the week".  You should see if you can submit it there.

---

