---
title: "can't install any ubuntu"
date: 2013-11-22
forum: Installation &amp; Upgrades
---

### Post by cmcanulty on 2013-11-22
I clean formatted an old laptop with the live usb and now can't install any ubuntu version it hangs every time at the page where you pick download updates while installing etc. Won't pick up ethernet or wireless connection.I t is a gatewayMA3 with 1 GB ram and 120 gb hd. I can get into the live session but if I pick install from there same hang happens.

---

### Post by mellocode on 2013-11-22
Are you sure the install on the live usb is good? Can you try it from a different source? I have had problems where if I created the usb disk from specific versions of Ubuntu or Mint it wouldn't install. I would try unetbootin or another version of Linux to create the usb startup disk if you can.

---

### Post by cmcanulty on 2013-11-22
I have tried several usbs and dvds I thunk it may be the no modset issue but I can't remember how to solve that

---

### Post by Bashing-om on 2013-11-22
cmcanulty; Hi again .

That "old laptop" do you know that the processor supports pae and sse2 ?
Else you will have to use the 'buntu distro that does not require pae and sse2 kernel.

To use  "nomodeset" :
As soon as the bios screen clears, hit the shift key -> language screen -> boot options screen -> f6 key. To the best of my poor memory at this point you should see a pop up of the boot parameters, arrow across and insert the boot option "nomodeset". I think the enter key takes you back to the install screen.

Now for the "try ubuntu" "nomodeset" option:
Boot the liveCD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; for other additions the boot options kernel boot line is now available, append any desired boot parameter to the end of the line.
Enter key to continue the boot process to the GUI desk top.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by cmcanulty on 2013-11-23
I tried the any key, esc, f6 with several ubuntu versions nothing happens just freezes still at preparing to install ubuntu I need to get to the f6 options somehow, thanks
I tried this but I get a boot prompt only and tried typing b43.blacklist=yes but nothing happened
also tried this
" Quote Originally Posted by MorrisseyJ View Post
Thanks Hubu,

I didn't have a backup so haven't tried your solution.

I did however get this working another way. So here is another detailed solution. It should work but you will need a wired internet connection.

First you need to blacklist b43 so that you can get into the live session.

1. Boot to the live CD/USB
2. When the screen comes up showing the accessibility icon (little stick man and keyboard at the bottom of the screen), press any key
3. Pick your language, press enter
4. Press F6, this will launch a dialogue
5. Press esc to get rid of the dialogue
6. You should now have a cursor from which you can enter commands below the boot options: Type making sure there is a space before and after the text you enter.
7. Press enter to either 'Try Ubuntu without installing' or 'Install Ubuntu'

In the case of the former, above, your instance of the live session should now work.

Now you should be able to install Ubuntu but you will still need to install b43 onto your system so that you can boot normally and use your wireless. To do this you have to boot to your system to do the install, but before that will work you once again have to blacklist b43 in the boot process. Here are the instructions.

1. Boot to the grub screen. If grub doesn't load automatically press, and hold, the Shift key after the BIOS screen (the screen mentioning your machine's manufacturer) disappears.
2. At the grub screen (the purple screen which lets you choose the instance of the kernel you want) press 'e', this will bring up a screen of text.
3. Using the arrow keys, navigate to the line which ends with "vt.handoff" or something similar. At the end of that line enter again making sure to leave spaces before and after.
4. Press F10

This should boot you to your install, but your wireless won't be working. To fix this we have to install b43

1. Open a terminal (ctrl+alt+t or hit the 'super-key' (the one with the windows logo on it) and type 'terminal' and press enter).
2. Enter 3. Enter your password (note your keystrokes won't register) and hit enter

Now b43 should install, your wireless should work and you should be able to boot without any problems.

Thanks to different people who helped me sort this out. Also, here is a blog detailing much of what needs to be done and which helped me get this sorted: http://linux-software-news-tutorials...s-because.html"

I am stuck

---

### Post by Bashing-om on 2013-11-23
cmcanulty; Good morning !

Old hardware/installs: See if these are relevant:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

Means and woes:
[http://ubuntuforums.org/showthread.php?t=1959675](http://ubuntuforums.org/showthread.php?t=1959675)

and some options:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1072311](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1072311)

So we need to find something that will boot.. say Lubuntu ?

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by cmcanulty on 2013-11-23
I tried lubuntu also. This machine had ubuntu on it (12.04) and wanted a clean install of Xubuntu 13.10. Before I always had to tweak the nomodset or blacxklist b43 but now I can't get f6 to bring up the options. it is a 64 bit processor. so I don't think PAE is an issue. I can get to the live install is there a way to fix this from the live session?

---

### Post by Bucky Ball on 2013-11-23
Don't go for updates and try to get online. Just install from the disk and tweak the internet problem when you have an installation in and a desktop. The cable will probably connect at that point, with any luck.

---

### Post by cmcanulty on 2013-11-23
I can't wait until it installs to get on internet as it hangs every time at the page where you pick download updates while installing etc.

Got it! I wasn't clear that I had to uncheck both updates and 3rd party software and then it installed and I blacklisted b43 then installed b43. Now I have wireless working also , thanks sorry to be so dense!

---

### Post by Bucky Ball on 2013-11-23
Good news. ;)

---

