---
title: "Ubunto 7.04 install fail"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by Imkenbo on 2007-09-08
Have a laptop with Windows on it but broken cd so I tried UNetbootin to get ubuntu instlled - all went fine until grub - complained it couldnt install - then CRASH

reboot now takes me to a grup prompt - what now?

---

### Post by wolfen69 on 2007-09-08
i dont know what Unetbootin is, but have you tried installing from a cd?

---

### Post by Imkenbo on 2007-09-08
software allows install form net and my cd drive is broken

---

### Post by Pumalite on 2007-09-08
Post specs.

---

### Post by Imkenbo on 2007-09-08
Hi-Grade Ultinote M6600 P4 2.4 1gb 60gb hd

---

### Post by Pumalite on 2007-09-08
Graphics is usually the most important part. I suspect you should use an Alternate CD.

---

### Post by Imkenbo on 2007-09-09
ahh.. It's not the CD that's broken it's the cd drive- no cd will work with it

---

### Post by merlinus on 2007-09-09
Are you seeing a menu, or just something like this:

grub>

If this, then try entering these commands, one at a time:

find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

Substitute results from find for (hdx,y) and setup (hdx).

So, for example, if find returns (hd0,1), then root will be (hd0,1) and setup (hd0).

If this works, then restart.

---

### Post by Imkenbo on 2007-09-09
so far so good - what next - it came back with (hd0,0) I ran all the commands and they were successful

when I reboot it just comes back to the same place

---

### Post by Pumalite on 2007-09-09
> **Imkenbo said:**
> software allows install form net and my cd drive is broken

Network Install

For those people using a Windows machine as the source for a network install, it can be done. Hopefully below will help someone one day with this exact scenario.

1 - Use TFTP.exe to serve as a network boot DHCP (instructions at this post) - [http://hugi.to/blog/archive/2006/12/...ll-via-windows](http://hugi.to/blog/archive/2006/12/...ll-via-windows)

2 - Disable IIS (temporarily) - IIS has problems with some of the file name and file structures

3 - Extract the ISO to a folder on your harddrive (approx 7.5GB of space needed)

3 - Install Apache HTTP, edit the http.conf file change the "Document Root" (line 149) to the folder on your harddrive where you extracted Ubuntu and also change line 177 to the same directory. Do not use backslashes eg. c:\ubuntu must be in the http.conf file as c:/ubuntu

4 - Around line 203 of the http.conf file add "Allow from x.x.x.x" where XXX is the IP address of the computer you are installing from. OR (but be careful) you can say "Allow from all"

5 - Check that you can access this in your browser. (depends on how you config'd your apache)

5 - Then start TFTP.exe

6 - Set the remote machine to boot from network (check in your bios settings)

7 - It should boot from network and start installing.

A couple of posts that helped me out (which may help someone else in turn one day):
-----------------------------------------------------------------------------------
[https://help.ubuntu.com/community/In...sServerNetboot](https://help.ubuntu.com/community/In...sServerNetboot)
[http://hugi.to/blog/archive/2006/12/...ll-via-windows](http://hugi.to/blog/archive/2006/12/...ll-via-windows)
[http://ubuntuforums.org/showthread.php?t=332343](http://ubuntuforums.org/showthread.php?t=332343)
[https://help.ubuntu.com/community/In...on/FromWindows](https://help.ubuntu.com/community/In...on/FromWindows)

---

### Post by Imkenbo on 2007-09-09
I'm past that bit
Linux partitions created - software downloaded and installed
Was at the bit at the end where it sets up grub and the boot stuff when it crashed

All I need - I think - is how to setup grub from a grub> prompt and then reboot

---

### Post by Pumalite on 2007-09-09
Merlinus told you how to do it in post #8. It seems to succeed. I had the impression for what you said in post #9 that the installation had failed and that you had to do it all over again.

---

### Post by Imkenbo on 2007-09-09
I did everyting merlinus said and got no errors but reboot took me back to the same place

---

### Post by Pumalite on 2007-09-09
Well you have no way to check if you have a system installed. You followed merlinus advice, you ended up in the same place, Chances are you don't have a system installed. I'd say do it all over again to make sure you get it right this time.

---

### Post by Imkenbo on 2007-09-09
maybe I'm being stupid but I now have a box with no os then and no way to get one on thanks to a grub installer failing.
What's even more heartening - is you can run a grub installer - get success all the way through but it does nothing useful at the end of the day.

---

### Post by Pumalite on 2007-09-09
Grub is a bootloader. It cannot install itself where there is no ssystem

---

### Post by Imkenbo on 2007-09-09
so me running the stuff below is right but I still have no OS

find /boot/grub/stage1  >>> returning (hd0,0)

then

root (hd0,0)  >> returns nothing

then

setup (hd0)  >> returns
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded. succeeded
Runnnig "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

then

quit  >> Error 27: Unrecognised command

Is not right and I have nothing for my "the benefits of linux presentation tomorrow"...

---

### Post by merlinus on 2007-09-09
Did you enter this at a grub prompt --  >grub  -- or at a command line?

If the latter, then start with:

sudo grub

to get to the grub prompt, and then enter the rest of the commands.

---

### Post by Imkenbo on 2007-09-09
tracked it down

was bad sectors on the boot strap - sorted it with spinwrite then tried again (5th of today)

and it worked  --  thx to all that helped

---

### Post by merlinus on 2007-09-09
Wonderful news!  Gotta love those success stories.  Well-done!

---

### Post by Pumalite on 2007-09-09
I agree. Pheew!

---

