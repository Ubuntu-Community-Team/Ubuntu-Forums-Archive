---
title: "Dual boot problem after in-Windows installation"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by komponisto on 2008-08-16
Hello everyone!

This is my first post, I have tried the local Swedish forum but no-one there can give me a sufficient answear. I hope you guys can! :) I have scanned the forum for some other thread that deals with my problem, but I can't find it (if someone does, please share!).

Well, the thing is: I'm trying to convince my very suspicious dad to start using Linux. He's a very conservative Windows-user, but since even he can see that my mom's Ubuntu-powered laptop is working just fine, he agreed to get enlightened.

I thought that the new in-Windows way of installation that is included on the Hardy-CD could be OK to use, just to show him how it works.
My dad thought that Xubuntu looked nicer than Ubuntu so I picked a Live-CD and started to get busy.
Everything worked just nice, I installed the files on a brand new (well...) harddrive so that removing the OS wouldn't be such a fuzz. When the installation program asked me to reboot the whole thing I agreed. But when the dual-boot menu appears and I select "Xubuntu" the only thing that happens is that GRUB starts saying:
```
grub>
```...or something similar.

It seems that GRUB wants me to write something, but what? I thought that the fact that I installed Xubuntu on another harddrive than Windows caused the problem, so I tried to uninstall from Windows (no problem there) but nothing happens when I click the uninstall-file. I also tried the "Remove applications" (or what ever the name is) from the control panel, but alas, the same thing there: Nothing happens.

Does anyone have an idea what I should do?

/Robin

---

### Post by kflorek on 2008-08-16
I can guess.

Something on the grub menu is wrong. Probably it points to the wrong hard drive, since you have two, or it doesn't have anything at all but the title.

 To find out, either press e (for edit) to take a look at what is actually on the Xubuntu menu. (Or if that does nothing, press ESC to get to the non-graphic menu first. Then press e with Xubuntu selected) It should look something like mine:

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,9)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=667bde05-59f1-4f46-91bc-91af59c3f13f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

although I have Ubuntu, not Xubuntu. If it looks something like this, the key thing to look at is

root		(hd1,9)

On mine, hd1 is the the second hard drive. And Ubuntu is on partition 10. GRUB always has the number one less than actual, because it counts starting with 0 instead of 1.

Most likely on yours it should be

root		(hd1,4)

or

root		(hd1,0)

 If not, select the line and press e for edit. And Enter when you have it OK. Then press b (for boot). Try both of these, and then other numbers until you might hit it.  If this works and linux boots, then you edit /boot/grub/menu.lst to correct.

But if the menu doesn't look anything like mine, things get more complicated.

Hope this helps. I don't check the forums often, so I may not be back.

---

