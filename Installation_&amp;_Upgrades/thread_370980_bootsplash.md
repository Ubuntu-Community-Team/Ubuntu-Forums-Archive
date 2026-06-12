---
title: "bootsplash"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by dmsn on 2007-02-26
Hey
I dont get my bootsplash to work :/

dmsn@laptop:~$ sudo apt-get install splashy splashy-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package splashy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package splashy has no installation candidate
dmsn@laptop:~$ 

Why doesnt it work?

Thanks

---

### Post by solar george on 2007-02-26
Ubuntu uses usplash which is installed by default.


Enable all of the repositories and then do
```
sudo apt-get update
```
 and try again.

---

### Post by dmsn on 2007-02-26
[LEFT]Already tested that many times.[/LEFT]

---

### Post by dannyboy79 on 2007-02-26
are you saying that you want additional splash stuff to occur or are you saying that the default splash screen isn't working? if the default isn't working it may be because it got turned off in your boot line within your menu.lst because I know I turned mine off, I like to see the messages that flash by to make sure there aren't any issues that I may not know about. so check your /boot/grub/menu.lst file, then look at all the lines like this:
kernel          /vmlinuz-2.6.15-28-686 root=/dev/hdc2 ro noapic
notice how I don't have splash, that's because I don't want to see the splash screen. if you want more splash screens that I can't help you? if your default doesn't work, try adding "splash" onto the end of your current line, make sure you have a space between splash and the previous last boot option. good luck.

---

### Post by dmsn on 2007-02-26
My menu.lst

title           Ubuntu, kernel 2.6.20-dmsn
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-dmsn root=/dev/sda2 ro quiet splash 
savedefault
boot

---

### Post by johnc4510 on 2007-02-26
dmsn, it looks like that package is no longer available according to the terminal text with your first post. I have included a window shot of the splash packages available for edgy with all repositories enabled. You can also get more splash images @ gnome-look.org

Now, do you know how to change the splash image once you have a new one installed? I will help you if you don't.

---

### Post by dannyboy79 on 2007-02-26
> **dmsn said:**
> My menu.lst

title           Ubuntu, kernel 2.6.20-dmsn
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-dmsn root=/dev/sda2 ro quiet splash 
savedefault
boot

are you running edgy or fiesty? also, you didn't answer my question? you didn't say whether you wanted more splash thingys or if your default splash screen wasn't working?

---

### Post by dmsn on 2007-02-26
I have Edgy.
I have the stuff installed as your picture.
I want just the default bootsplash like what i had in default generic kernel.

---

### Post by dannyboy79 on 2007-02-26
when you do 
locate splash

what shows up? is there anything you're not tellling us, like maybe you used bum (boot up manager) to disable it or to turn off some services that start doing boot up? I just don't understand why this isn't working? what did you do and when did it stop working?

---

### Post by dmsn on 2007-02-26
Well it works when i use my old default generic kernel.
Just not my own configured kernel 2.6.20.
locate splash get alot of directories.

---

### Post by dannyboy79 on 2007-02-27
ahhhhhh, well you never said that. at least I didn't read that if you did post that. this is a different story now I would say. I have no idea what to tell you? i found this using gogle, it was in the instructions for compiling a custom kernel, I don't know if this applies to 2.6.20 though?
"download latest 2.6.11.6 vanilla configure aind install (without initrd, but it is not needed here, you will lose splash screen. Personally I don't like it anyway because I want to know what is failing to start)"
well, the locations that were found when you did locate splash, did you find /etc/init.d/usplash? also, do you have these symlinks to that?
/etc/rc2.d/S98usplash
/etc/rc3.d/S98usplash
/etc/rc4.d/S98usplash
/etc/rc5.d/S98usplash

---

