---
title: "[SOLVED] ubuntu installed one laptop - used on another = ?"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by jeppex on 2008-01-12
Hi
The cdrom drive of my standard laptop doesnt work so I moved my hard disc temporarily into another computer, installed Ubuntu, and moved the hard disc back to the standard laptop.
No graphical interface, so I reconfigured xorg. (dpkg-reconfigure...)
But still when I boot there are no output (text nor graphic) from grub menu to login screen. That makes me wonder if anything else needs to be reconfigured, chipset or something...?

Jeppex

---

### Post by Arthur Archnix on 2008-01-12
You can apparently get to a terminal then, if you can reconfigure x. What errors are you getting? Do you get to the gdm, or does it give an error and spit you into a non-x session? You can try editing the boot option, go into grub, press 'e' on the normal boot option. Find the kernel line and remove 'quiet'. Hit 'esc' and then 'b' to boot.

---

### Post by jeppex on 2008-01-13
I'll try to put into more clear terms:

My cdrom drive is broken on my Dell Inspiron laptop and i wanted to switch back to Ubuntu from Mint.
So I switched the hard disc from my Dell into a Siemens Amilo. Installed Ubuntu, switched back the hard disc to my Dell and booted. It couldn't start up X, so i reconfigured it by typing
```
dpkg-reconfigure xserver-xorg
```
I edited the configuration to make it fit to my ATI and X was up and running.

But then i figure that, since I manually had to reconfigure my graphics, other things might have to be reconfigured as well. One problem I have experienced, and thus far the only, is that it takes my pc almost 3 minutes to boot from the GRUB menu to the login screen. With Linux Mint it took about 1 minute and that is alomst the same system. AND from the first bit of text after the GRUB I see no text nor splash until the login.

I've tried editing /boot/grub/menu.lst. Before the last part looked like this:
```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0e455bd4-c20b-4a62-8336-7289ecaae794 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0e455bd4-c20b-4a62-8336-7289ecaae794 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Now it lookes like this:
```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 vga=771 ro splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0e455bd4-c20b-4a62-8336-7289ecaae794 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Do anyone have any ideas of what might be the issue here?

---

### Post by jeppex on 2008-01-13
Oh by the way, that editing of boot/grub/menu.lst neither solved nor changed nothing.

---

### Post by Arthur Archnix on 2008-01-13
Something that I've noticed, and I posted a question on the forums to this effect, was that since Feisty some kind of change has been made whereby I used to be able to add vga options to my grub and remove quiet and splash, and then I'd get a text mode boot. Since Gutsy I can't do that anymore and I see symptoms just like what you're describing.

In the end I just ended up doing a clean install, then I stopped messing around with my grub boot splash. Not really an option for you though. I would start by removing the vga option that you added to your boot line parameters. Then I would go into synaptic and completely remove the usplash. Another way would be to type in a terminal
```
sudo apt-get remove --purge usplash
```
Then reboot and see what has changed. After that I'd reinstall usplash
```
sudo apt-get install usplash
```
Removing and reinstalling automatically regenerates some boot config files and may solve your problem. 

As for the long boot time, after logging in, post the output of
```
dmesg
```
dmesg is a log of your last bootup and the first place to start a search for what's taking so long.

---

### Post by jeppex on 2008-01-14
Thank you for that. After removing usplash it only took me 30 sec from exiting GRUB to getting to the login screen.
But still I don't get any splash screen. Even after reinstalling usplash

---

### Post by Arthur Archnix on 2008-01-14
Ok, well good to hear the bootup speed is better. I expected usplash to fix the splash image and then for the bootup speed to need fixing, so my advice did the exact opposite of what I thought it would do. Take that into consideration as we go forward. :P

Anyway, dmesg isn't needed when bootup speed is normal. You can remove it from your last post. As I said in my last post I ended up needing to reinstall. Why don't you try going into synaptic and searching for usplash. When you see usplash-theme-ubuntu completely remove it and reboot. Then reinstall it and reboot. Then if it's still not working post your grub menu again so we can take a look at the latest  version of it.

Edit: Found this on another [thread]("http://ubuntuforums.org/showthread.php?t=580903")

> Does the black Ubuntu loading splash screen work when you do that?

If not, here is another (slightly longer) fix that was posted elsewhere to fix it for reals. The problem with the slow boot is that the settings in Usplash can sometimes get messed up on install and hang up the boot. Removing some of the lines in menu.lst disables Usplash and fixes the problem. If you like the verbose boot up, then leave it. If you'd like the pretty Ubuntu boot up sequence, try this.

1) Put everything back in /boot/grub/menu.lst that you took out ( "ro quiet splash" in the kernel line and "quiet" at the end)

2) At the very end of the kernel line after "splash" , add "vga=791" This is the weird part for me, because I'm not exactly sure why the number is 791. Make sure this goes on the same line, though.

3) Save that file, close it, and open up /etc/usplash.conf

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

uname -r
This lists your current kernel version.

sudo update-initramfs -u -k <insert results from uname -r here>

This rebuilds the image that Grub uses to start the system.

Voila, you have fixed the boot speed issue and gotten the splash screen back. Reboot and enjoy the fruits of your labor. Your mileage may vary, but it worked for me on the first try and for quite a few other people throughout the forum. This only works if Usplash is what was broken, which sounds right for all of you. Also, you can always hit CTRL-F1 when the splash is running to get back to your verbose mode.

---

### Post by jeppex on 2008-01-18
talk about easy solutions. Yet again. usplash-theme wasnt installed, so I did so, and the splash appeared both at shut down and start up. So that kind of fixed it. You've been very helpful.

So now I think everything is ok. Unless you can recommend a way to test, if the alternate installation has prompted other potential problems.

But thanks!

---

### Post by Arthur Archnix on 2008-01-18
```
apt-get install magik-8-ball
bash>Any more problems?
apt-get shake magik-8-ball
bash>print magik-8-ball

```
:wink:

The great thing about Ubuntu is that they build their kernels with pretty much everything loaded as a module. That's why you can install it on one computer, unplug the disk and boot on another computer with little problems aside from xorg config, that you solved straight away.

I'd never actually seen it done though, so thanks for showing me what's possible. If we've nailed down your current problem though, you can mark the thread solved using 'thread tools' to help future users...who have two laptops...one of which doesn't have a working cd rom. :-\"

---

