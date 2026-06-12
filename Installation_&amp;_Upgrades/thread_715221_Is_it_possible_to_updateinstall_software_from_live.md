---
title: "Is it possible to update/install software from live cd?"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by Front187 on 2008-03-04
Is it possible to update/install packages to my linux hard drive partition via a live cd?

If so, is there a special way to do it, or will the live cd recognize that I have a linux partition installed and use the proper directory paths?

EDIT FOR CLARITY ( I AM NOT ASKING ABOUT USING THE CD AS A REPOSITORY):

I apologize, I was unclear.

I would like to know if I can boot my computer into a live CD, and then from inside this CD based environment install a package to the filesystem located on my harddrive.

---

### Post by Pumalite on 2008-03-04
Some programs are in the  Live CD, most are not. When you try to install a program in your system, if it is in the Live CD, your system will ask you to insert your Live CD. Otherwise will do it through the repositories.

---

### Post by ryanhaigh on 2008-03-04
I thought that the livecd was essentially just an image and contained almost no packages. Just checking the alpha5 of hardy seems to confirm this. As far as I remember you can actually use the alternate cd as a package source and it will contain a lot more packages. You can also use a program called AptOnCd whichn allows you to create a cd of the packages from a system you have already fully installed/updated.

Once you insert the cd open the terminal and use:
```

sudo apt-cdrom add

```

Ubuntu may have a nice GUI that does this automatically now but I have never used it so cannot be certain.

---

### Post by aysiu on 2008-03-04
The live CD is an image and contains almost no packages, as ryanhaigh suspected.

---

### Post by Front187 on 2008-03-04
I apologize, I was unclear.

I would like to know if I can boot my computer into a live CD, and then from inside this CD based environment install a package to the filesystem located on my harddrive.

---

### Post by Pumalite on 2008-03-04
You got Aysiu's answer.

---

### Post by aysiu on 2008-03-04
> **Front187 said:**
> I apologize, I was unclear.

I would like to know if I can boot my computer into a live CD, and then from inside this CD based environment install a package to the filesystem located on my harddrive.
I don't know the details of it, but I believe something called *chroot* might help you with that. If I understand it correctly, the command allows you to (from a live CD session) pretend you are actually working with the hard drive filesystem.

Can you tell us a bit more about your situation?

---

### Post by Front187 on 2008-03-04
I can, though I was trying to avoid it, because I'm a bit embarassed of it.

I've accidentally removed vmlinuz*** from my /boot directory, and I believe I need to reinstall the kernel package.  This obviously becomes a bit more complicated when it is impossible to boot into your operating system.

EDIT:  I've looked up chroot, and this looks like it might be the answer to my problem.  

Maybe it's good that I did this, because if it works the way I understand it to, then I have learned a very powerful command that I can use for troubleshooting/recovery. :)

---

### Post by Front187 on 2008-03-04
SOLVED

Yes, it is infact possible with chroot! :)  

Thanks to aysiu for the suggestion.

```
#Live cd enviornment

sudo su
mkdir /media/root
mount -t ext /dev/sd[a-z][1-N] /media/root
chroot /media/root apt-get install linux-386


```

Simple as that! :)

---

