---
title: "Installing Ubuntu 10.04 Alternative - editing Grub?"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by whitefish10 on 2010-10-08
Hi guys, I am currently installing the Ubuntu 10.04 Alternative, as I am having problem with video card.

What I know is that I need to edit the Grub file in /etc/default/grub and add i915.modeset=1 for my video card.

What I don't know is how to do that in the command line, what application should I use and how to save it? Also, if everything works well, I want to boot to gnome automatically.

What I am looking for is a step by step instructions (as I can get lost).

Thanks.

---

### Post by drs305 on 2010-10-08
That setting would be placed in /etc/default/grub. Open a terminal: Applications, Accessories, Terminal.

Open with a text editor as root *:
```
gksudo gedit /etc/default/grub
```

Add it to the following line and save the file.
> GRUB_CMDLINE_LINUX="i915.modeset=1"

Then update Grub2:
```
sudo update-grub
```

* If you can't boot into your installation we will have to do it via other means. Just let us know.

---

### Post by whitefish10 on 2010-10-08
> * If you can't boot into your installation we will have to do it via other means. Just let us know.

Yes, I cant boot. How can I fix this?

---

### Post by drs305 on 2010-10-08
I have typed up instructions but before I post them we might be able to do this in a simpler manner.

Have you already completely installed Ubuntu? There is a way to add special commands during the installation, but if you have already installed that's ok.

Can you see the Grub2 menu during boot? If you can, we can edit the menu the first time. Then it will be very easy to make the changes.

If you don't see the Grub2 menu, try holding down the SHIFT key early in the boot process. Does the Grub2 menu appear now?

---

### Post by whitefish10 on 2010-10-08
I hold down the SHIFT key and it gave me the GRUB2 menu, pressed E to edit, and I don't know what to do next?

---

### Post by drs305 on 2010-10-08
> **whitefish10 said:**
> I hold down the SHIFT key and it gave me the GRUB2 menu, pressed E to edit, and I don't know what to do next?

That's ok. It's pretty simple.

With the menu entry open for editing, cursor to the end of the "linux" line. It probably ends with "quiet splash". Just add **i915.modeset=1** and then CTRL-x to boot.

I can't guarantee the option will work, but that is how and where you add it.

Now, once it boots, follow the instructions I put in Post #2 to make the option permanent.

---

### Post by whitefish10 on 2010-10-08
I deleted the "quiet splash" and replace it with i915.modeset=1, and now is working!!!!:D. Thank GOD.

So every time I am going to boot the machine it will boot to gnome automatically?

one more thing, I was having a previous partition when I was running fedora with a mounting point of /home, I was having some files there, I didn't delete it but I mount it again with Ubuntu, so far right now I can't find anything?

---

### Post by Rubi1200 on 2010-10-08
Now that you are back in Ubuntu please post the output of```
 lspci | grep VGA
```Since you have an Intel chipset there may be a fix to make the setup more permanent. The suggestion above by drs305 to edit the GRUB file also works, but see here for other options:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

I have successfully used the workarounds from the link above and can offer help in that direction if you wish.

Thanks.

---

### Post by drs305 on 2010-10-08
> **whitefish10 said:**
> I deleted the "quiet splash" and replace it with i915.modeset=1, and now is working!!!!:D. Thank GOD.
:-)

> So every time I am going to boot the machine it will boot to gnome automatically?
If you aren't seeing the menu on boot, try placing a # at the start of the "GRUB_HIDDEN_TIMEOUT=0" line:
> **#**GRUB_HIDDEN_TIMEOUT=0

If you want to have a longer timeout, or wish to change the default OS, take a look at the "G2-Tasks" link in my signature line. It explains how to make those changes. You can also change the timeout or default OS with StartUp-Manager. Information about this GUI app is in the "SUM" link below.

> one more thing, I was having a previous partition when I was running fedora with a mounting point of /home, I was having some files there, I didn't delete it but I mount it again with Ubuntu, so far right now I can't find anything?

From a normal boot, if you don't see the Fedora partition in Nautilus Places, make a mountpoint and mount the partition manually:
```
sudo mkdir /mnt/fedora
sudo chown -R <yourusername>: /mnt/fedora
sudo mount /dev/sdXY /mnt/fedora  # XY is the drive/partition of fedora home (sda5, sdb4, etc)
```

---

