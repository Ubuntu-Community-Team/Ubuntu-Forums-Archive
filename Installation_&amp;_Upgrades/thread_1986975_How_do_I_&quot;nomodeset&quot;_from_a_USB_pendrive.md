---
title: "How do I &quot;nomodeset&quot; from a USB pendrive?"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by LancerNZ on 2012-05-25
My computer uses an Nvidia card. It's certainly not old hardware (built from parts by order just this year). But with Ubuntu 12.04 LTS (which I am booting to in order to rescue a bawked Update job), they changed something so that if I were to run Grub, I would have to insert "nomodeset" into the script or face a black screen, locked keyboard etc.

When running a live-CD, I can also opt to use "nomodeset" by hitting any key as the system starts (when the keyboard and person show at the bottom of the screen), choose my language, and the [F6] to access the option (ESC to close). That's good.

But... if I boot from a USB pendrive made how Ubuntu recommends on their as per these instructions: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows) ... then the USB appears to have no such option?

Can someone please let me know how I can use the "nomodeset" option when booting from the USB? I would like to know for USB drive because these are much faster and more reliable than booting from CD-Rom.

---

### Post by darkod on 2012-05-25
If I am not mistaken, that procedure replaces the standard menu. Do you get any menu at all when booting? Like a simplified grub/syslinux menu?

---

### Post by VMC on 2012-05-25
Booting from either cd or usb should be the same. Hit F6 and you should see the "linux" string at the bottom. Just go the the end and add "nomodeset".

You are talking about the usb live install, yes?

---

### Post by LancerNZ on 2012-05-25
I do get a simplified boot menu; but I can't see any method to insert the nomodeset option I know my computer needs.

Only...
[LIST]
[*]Run Ubuntu from this USB
[*]Install Ubuntu on a Hard Disk
[*]Test memory
[*]Boot from first hard disk
[*]Advanced options => (nothing)
[*]Help
[/LIST]

I can do it from the CD-Rom boot as I showed in detail above, but the option doesn't appear to be there on a USB made from link I previously gave, so no... they are not the same.

---

### Post by oldfred on 2012-05-25
I have this in my notes, but have never used it as I loopmount ISO directly and added in the grub command.

USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 



I think you can also add it to the syslinux menu on the USB like this:

If booting from USB it just may be easier to edit syslinux with whatever boot parameters you need like this:
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
[http://blog.bodhizazen.net/](http://blog.bodhizazen.net/)
simply edit “syslinux.cfg”

---

### Post by darkod on 2012-05-25
Even when it doesn't say so, you should be able to edit the boot lines with 'e'.

Highlight "Run Ubuntu from this USB" and try hitting 'e'. If that shows you the boot lines, simply add nomodeset in front of the 'quiet splash'.

EDIT PS. oldfred is right, it might be TAB to enter the edit mode.

---

### Post by LancerNZ on 2012-05-25
Thank you ;)

The [Tab] button does work.

I also found that if making the USB drive under the Ubuntu method (as opposed to through Windows) you end up with a boot up just like the CD-Rom where the steps as I was expecting are intact. I was able to boot from CD-Rom and create a less feature-hidden USB this way.


Ubuntu method here: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

---

### Post by darkod on 2012-05-25
Yes, I would say the startup disk creator is always better, as long as you have a machine running ubuntu to create it on.

---

