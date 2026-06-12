---
title: "GRUB Bootup Error"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by twinkeir on 2011-06-21
So Ubuntu has been working fine for me. I had the latest version (which is 11.04) and updated everything. I rebooted and it worked fine for a few days.

Then when trying to boot Ubuntu I get this error

```

Try (hd0,0) : NTFS5 : 
error: "prefix" is not set.
error: no such device /ubuntu/disks/root.disk

```Then I get one more error which I didn't have time to right down and then the GRUB console comes up. Like this one[B]

[http://plugintolinux.ca/files/slideshows/grub/img3.jpg](http://plugintolinux.ca/files/slideshows/grub/img3.jpg)[/B]

I cannot boot Ubuntu at all. I have Windows 7 professional running along side it and it works perfectly. I installed using the latest version of **Wubi**.

Ubuntu Details -

[LIST]
[*]One User Account Only
[*]That account is password protected, yes I do know the password
[*]I selected **17GB** in Wubi for the size.
[/LIST]

Also this is a completely differant queston. Is it posible to have Windows 7/Ubuntu and Kubuntu so the computer would be triple booted?

Thanks
Keir

---

### Post by Rubi1200 on 2011-06-21
Hi and welcome to the forums :-)

This is what you need to do:

When the computer starts and you see the entry for Ubuntu press "c" to drop to a grub prompt (the one you posted an image of).

Then enter these commands and post the output here:

```
search -s -f -n /ubuntu/disks/root.disk
echo $root
```After this type "reboot" and go back to Windows.

In Windows, make a backup copy of the root.disk and place it somewhere safe like an external medium (USB stick etc.).

Once we have the output of the commands above, we can proceed.

---

### Post by twinkeir on 2011-06-21
I managed to get the 3rd error I talked about.

```

error: no such device : /ubuntu/disks/root.disk

```Output:

```

*search -s -f -n /ubuntu/disks/root.disk*
error: no such device : /ubuntu/disks/root.disk
[I]echo $root
[/I]memdisk
```

I cannot find that file. On the C:\ drive there is a ubuntu folder but no disks folder.
Screenshot: [http://dl.dropbox.com/u/16989182/screenshot.PNG](http://dl.dropbox.com/u/16989182/screenshot.PNG)

Thanks
Keir

---

### Post by Rubi1200 on 2011-06-21
You don't appear to have an /disks folder; do you know what might have happened to cause this?

You need to enable the option to view Hidden Files and Folders:
[http://www.bleepingcomputer.com/tutorials/tutorial151.html](http://www.bleepingcomputer.com/tutorials/tutorial151.html)

Once you have done that, look for a folder called  C:\found.000 (or similar). If you find the root.disk and swap.disk files there move them back to the root of the C drive and place them in their correct file structure:

/ubuntu/disks/root.disk
/ubuntu/disks/swap.disk

Then try booting again. Also make sure the wubildr and wubildr.mbr files are at the root of the C drive.

---

### Post by twinkeir on 2011-06-21
> **Rubi1200 said:**
> You don't appear to have an /disks folder; do you know what might have happened to cause this?

You need to enable the option to view Hidden Files and Folders:
[http://www.bleepingcomputer.com/tutorials/tutorial151.html](http://www.bleepingcomputer.com/tutorials/tutorial151.html)

Once you have done that, look for a folder called  C:\found.000 (or similar). If you find the root.disk and swap.disk files there move them back to the root of the C drive and place them in their correct file structure:

/ubuntu/disks/root.disk
/ubuntu/disks/swap.disk

Then try booting again. Also make sure the wubildr and wubildr.mbr files are at the root of the C drive.

Followed the instructions. Found the folder found.000. It is just copying now (16.6GB)
Do I need the boot folder? The boot folder is empty apart from another empty folder called grub. If I do need it where do I put it?

To be able to open the folder I had to use the **Take Ownership **tweak. Will keep you updated. wubildr and wubildr.mbr are in the root of C:\.

Thanks for your help so far
Keir

---

### Post by Rubi1200 on 2011-06-21
I don't believe you need those empty folders, only the ones I mentioned.

Let me know what happens.

---

### Post by twinkeir on 2011-06-21
> **Rubi1200 said:**
> I don't believe you need those empty folders, only the ones I mentioned.

Let me know what happens.

Okay! Almost done!

---

### Post by twinkeir on 2011-06-21
THANK YOU SOOOOO MUCH!!!!

It is working now! I do not know what caused it. I am replying to this thread from Ubuntu. THANKS!

If you ever need a hand with your PC I can always give you a hand. It would have to be done online though.

---

### Post by Rubi1200 on 2011-06-21
Excellent! I am really pleased things are sorted out. 

You're welcome for the help :-)

Please mark this Solved using the Thread Tools near the top of the page.

Last tip: make a backup copy of the root.disk as I mentioned previously just in case this ever happens again.

---

### Post by twinkeir on 2011-06-21
> **Rubi1200 said:**
> Excellent! I am really pleased things are sorted out. 

You're welcome for the help :-)

Please mark this Solved using the Thread Tools near the top of the page.

Last tip: make a backup copy of the root.disk as I mentioned previously just in case this ever happens again.

Okay will do! Does the swap.disk and root.disk ever change? Or can I make a backup everytime I upgrade only?

---

### Post by Rubi1200 on 2011-06-21
Thanks for marking this Solved.

To answer your question:

you only need to backup the root.disk not the swap disk (though you could also make a copy just to have one).

If you are making frequent changes to the Ubuntu install such as downloading and installing software, saving files etc. then backups of the root.disk should be ongoing because the root.disk is being constantly modified. 

If, however, you are saving personal files outside the root.disk then you can probably do backups less frequently since not much is changing and because backing up like this also means backing up any free space on the root.disk.

Plus, as you saw, it is a rather large file!

If, at some point, you would be interested in migrating the Wubi install to a regular partition on your hard-drive, let me know and I can point you in the right direction.

Wubi installs are great for trying/testing another operating system in a relatively safe way, but Wubi was never intended for long-term usage.

Anyway, good luck whatever you decide.

---

### Post by twinkeir on 2011-06-21
> **Rubi1200 said:**
> Thanks for marking this Solved.

To answer your question:

you only need to backup the root.disk not the swap disk (though you could also make a copy just to have one).

If you are making frequent changes to the Ubuntu install such as downloading and installing software, saving files etc. then backups of the root.disk should be ongoing because the root.disk is being constantly modified. 

If, however, you are saving personal files outside the root.disk then you can probably do backups less frequently since not much is changing and because backing up like this also means backing up any free space on the root.disk.

Plus, as you saw, it is a rather large file!

If, at some point, you would be interested in migrating the Wubi install to a regular partition on your hard-drive, let me know and I can point you in the right direction.

Wubi installs are great for trying/testing another operating system in a relatively safe way, but Wubi was never intended for long-term usage.

Anyway, good luck whatever you decide.

Awesome I will definitely ask if I need to. Is it possible to have Windows 7 & Ubuntu & Kubuntu installed with wuibi or a program like that?

---

### Post by Banyo on 2011-08-29
I had the same problem as this guy, I have followed the instructions of Rubi and Im replying from ubuntu, thanks mate for your help ;)

---

### Post by Rubi1200 on 2011-08-29
> **Banyo said:**
> I had the same problem as this guy, I have followed the instructions of Rubi and Im replying from ubuntu, thanks mate for your help ;)
Hi and welcome to the forums Banyo :-)

Glad you found this thread and that the solution worked for you.

Enjoy :-)

---

