---
title: "force resolution in grub"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by reddeth on 2007-08-24
(Jump to the very bottom to get my question, the next two paragraphs are just as much venting as background)

Ok, I popped in the LiveCD, booted up, hit Install (or whatever the first option is). I get just a blank, black screen, the monitors on but nothing. So I try again, same thing. From just trying different stuff I hit F4 (on the LiveCD's opening menu, its the VGA button), and select the 1680x1050 option, Ubuntu pops up just fine, start installing, everything works great.

So now everything is installed, I finish up my game of Majhong (sp), and go to reboot the system, up comes GRUB, select Ubuntu, same blank screen as when I first put in the LiveCD/Installation CD. So I'm led to beleive that its simply an issue of resolution, and for whatever reason, my monitor is deciding not to display, well, a damn thing. After searching around a bit a few people suggested hitting Ctrl+Alt+F1, or Alt+F1 to bring up a CLI, I tried, got nothing, still the same blank screen, etc etc.

Ok ok, all in all, is there a command I can put into the GRUB boot line that basically says "start Ubuntu in 1680x1050, and if xorg doesn't like it, xorg can suck it"?

Thanks for the help!

---

### Post by Herman on 2007-08-24
Hello reddeth,
If you're talking about the bootup resolution in GRUB, then you should read this great tutorial by Indras, [HOWTO: Change bootup resolution]("http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters") .
That should help you see what's going on while Ubuntu is booting, after that, the  operating system takes over and your video card and monitor should be under the control of the X-server. As far as I know, GRUB's boot-time parameters that you can pass to the kernel with GRUB commands are only good until the operating system boots, but I learn something new every day, so please feel welcome to correct me if I'm wrong.

Maybe I'm wrong already, here's a link I have for cheat codes from Knoppix, I haven't experimented with these, but close to the top of the page there's some you can try, one is: screen=1280x1024, maybe you could try adding that to your boot entry in GRUB, but modify it to: screen=1680x1050 and see if it helps you, here is the link, [http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
Is that what you mean?

I also have one computer with a 1680x1050 resolution monitor, it's an Acer AL2016W, and every time I install Debian or Ubuntu the same thing happens to mine too, black screen, no picture.
What I do is boot the Ubuntu Live CD again and mount the hard disk installed Ubuntu's file system. Then I use terminal commands to open the hard disk install's /etc/X11/xorg.conf file in gedit text editor and paste the right resolutions in the mode lines.
Then I reboot. That works for me every time.
If you want to try that, here's how to mount your hard disk installed Ubuntu in the Live CD and access some vital files that  occasionally need to be edited that way,  [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000] .
A useful command for finding out what resolutions your monitor can support is, [/COLOR][/COLOR][FONT=Bitstream Vera Sans Mono]sudo ddcprobe [/FONT]```
sudo ddcprobe 
```You should make a backup of the file before you edit it.
```
sudo cp /media/ubuntu/etc/X11/xorg.conf /media/ubuntu/etc/X11/xorg.conf_backup
```
Regards, Herman :)

---

### Post by reddeth on 2007-08-24
Thank you for the suggestions, I will be sure to get working on them. I realize the OS takes over when it boots up, however I get the feeling that theres an error somewhere in the process of GRUB closing and Ubuntu starting up, but before X starts (and my resolution becomes readable) it throws an error and everything freezes up. 

I'll try to force the resolution via the command line in GRUB when I get home from work tonight. 

I'd simply copy over the Xorg.conf file from the LiveCD but the problem is I can't get into a CLI at all! Which I feel helps indicate that its throwing an error and locking up the system and thats whats keeping me out of the terminal/command line.

Thanks again for the suggestions!

---

