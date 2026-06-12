---
title: "Installed Ubuntu 13.10, now can't access computer"
date: 2014-01-05
forum: Installation &amp; Upgrades
---

### Post by rocketboy777 on 2014-01-05
Hi guys,

I have recently purchased a new laptop, (ASUS F452E, 2 Gb RAM, 500Gb hard drive), it did have Windows 8 pre installed.  I decide to install Ubuntu 13.10 64 bit.  The instalation went well once I had turned off "Fast Boot" in the BIOS.  I did read somewhere that I should also turn off "Secure Boot", but I could not find it anywhere.

Ater installing Ubuntu 13.10 I rebooted the computer and when it restarted it looked as though I was about to get the Ubuntu splash screen but suddenly the screen went black and I get an error message up at the top of the screen, it only stays for about five seconds so I had to reboot several times to eventually get the whole message.

[SIZE=3]**Failed to load file amd_unicode/microcode_amd_fam16h.bin**[/SIZE]

I have done quite a bit of searching and the best I have managed to learn is that it appears the file "microcode_amd_fam16h.bin" may have been located incorrectly, unfortunately the solution provided required the user working in the terminal window, I say 'unfortunately' because I can't even get onto the computer let alone get to the terminal.

Can someone please advise me where to go from here.


Regards


Al

---

### Post by PopsTheSailor on 2014-01-05
Did you set it up as dual boot (MS 8 & Ubuntu) or just Ubuntu? Do you get the grub screen to select the OS? I don't know what the file you are missing is supposed to do but have you thought about trying a boot-repair disk?

---

### Post by rocketboy777 on 2014-01-08
Did you set it up as dual boot (MS 8 & Ubuntu) or just Ubuntu?  Do you get the grub screen to select the OS? I don't know what the file  you are missing is supposed to do but have you thought about trying a  boot-repair disk? 				 			
  			   		
 			 				 			 			 			 		
 	

Thanks for your response.

I did not set it up a dual boot, I set it up as just Ubuntu.
I do not get any "Please select your O/S" message, it just looks as though it is booting as per a normal instalation, the screen goes the colour of the Ubuntu splash screen, but only stays like that for less than two seconds and then goes blaxck and I get the above message.  I did not get any disks with the computer, just a reserved partition which was blowen away during the instal process.

Do you think I would get better results if I try to install one of the Linux Distros for older hardware; Ie DSL, EasyPeasy, Etc?

Please don't tell me I have got a $450:00 brick sitting on my desk.  :)

Al

---

### Post by rocketboy777 on 2014-01-10
Hello everyone,

Due to the lack of responses, I am wondering if I have put this into the correct forum.  Can someone please get back to me and let me know if it would get resolution a little more quickly if I were to stick it one of the other forums.

Incidently, regarding the above issue, I have tried compleely re-installing Ubuntu 13.10 from flash drive, it reads the usb port with no problems, it goes through the install again with no problems, it even recognises there is an existing installation of Ubuntu 13.10.  It appears to go through the installation with no problems, certainly with no error messages. Yet when I restart I get exactly same situation as described above, the error message I now get is word for word the same as the one above.

That noise you hear is me wailing with the tormented souls in Hell :-))

Al

---

### Post by jdeca57 on 2014-01-10
First of all you can find out if the distribution works on the hardware by using a live version of either DVD or usb. If that fails you really have a problem, due perhaps to the fact that the processor is fairly recent. With 2 GB of RAM you might also try the 32-bit version (standard download is 64-bit) Also, if the problem would be related to GUI, try Xubuntu or even Lubuntu. Last, once you get the PC to work with a live version of one of the mentioned versions, the road is easy: then it's just a question of reinstalling with the working version. It's a bit late for this advice, but always try out the live version first. You might avoid hardware incompatibility. After all, hardware isn't made with Linux in mind.

---

### Post by rocketboy777 on 2014-01-10
jdeca57, thank youfor such a prompt reply,

* Yes, if I had a modicum more sense than intelegence I would have tried to run a live version before I tried to install Ubuntu. 
* Regarding the advice about a 32 bit version of the distribution, I read somewhere that one is supposed to replace Win 8, (any flavour), with a 64 bit version of the particular distribution you are endeavouring to install - obviously not correct.
* It really surprises me that hardware manufacturers don't want to harvest as much of their particular market share as possible by catering to all facets of the home computer market; Linux, Mac, Win Doze.  But hey, what do I know?  I don't have an address in silly-con valley.
* It's almost midnight here (NZ), and Mr Sandman has been putting his sand in my eyes.  I will get back to you after I try a couple of live distros tomorrow.


Al

---

### Post by PopsTheSailor on 2014-01-10
Here are a few more thoughts, but first just try the live CDs it's the easiest way to see if your system will support Linux (can't imagine why it wouldn't)

1. I think (not positive) that all the linux versions that have "buntu" in their name are all based off the same code base. You might want to try something like Fedora or OpenSuse that aren't the same.
2. Ubuntu does have a beta version available which is their next LTS version scheduled for release in April. It is 14.04. If you have a brand new computer maybe you need the latest version. Again, can't imagine this to be the case. Just a thought.
3. Maybe something went wrong with your initial install. Have you tried just reinstalling again? (Again, try the live CD first)
4. How did you install the first time? I've only ever installed by first booting on a live CD / USB. If that's the way you installed then Ubuntu did run fine on your laptop
5. I did what you did once (blew away entire HDD including Toshiba's restore partition). As a last resort, you can put your tail between you legs and pay Asus for a set of recovery CDs. It hurt me bad to do that but I ended up giving Toshiba $30 for a set of recovery CDs. 

Good luck

---

### Post by jdeca57 on 2014-01-10
> **PopsTheSailor said:**
> Here are a few more thoughts, but first just try the live CDs it's the easiest way to see if your system will support Linux (can't imagine why it wouldn't)
...
5. I did what you did once (blew away entire HDD including Toshiba's restore partition). As a last resort, you can put your tail between you legs and pay Asus for a set of recovery CDs. It hurt me bad to do that but I ended up giving Toshiba $30 for a set of recovery CDs. 

Well, the processor in that PC is the E1-2100 from AMD and very curiously I bumped on [http://driverscollection.com/?H=E1-2100&By=AMD&SS=Linux%20x86_64](http://driverscollection.com/?H=E1-2100&By=AMD&SS=Linux%20x86_64) - it makes one wonder, the driver is released 18 sep 2013, would that have made it to 13.10?
I found this on [http://www.joycemayne.com.au/asus-f452ea-vx021h-laptop.html](http://www.joycemayne.com.au/asus-f452ea-vx021h-laptop.html) and this laptop seems to have the same specs as mentioned by the OP... shared graphics and touch-ready but no mention of the card. That is the second possible problem.
 So, I can imagine why this PC wouldn't work but your point 5 offers a way out. Personally I would make a backup from the OS before erasing it, but I'm afraid to ask whether he did that. ;-)

---

### Post by rocketboy777 on 2014-01-11
Pops & Jdeca57,

Thank you both very much for the help you are giving me, even though  I have not acchieved resolution to my problem yet, it is really good knowing  there are others "out there" who are trying to help me.

Here is the latest

I tried booting into a live distrabution on usb, the laptop doesn't have an optical drive.  I got further than I have previously, but unfortunately I still have  not managed to get to a desktop.

Instead I got a small window in the middle of the screen with the following three options :-
(1) Review the Xserver log file, 
(2) Review the startup errors, 
(3) Edit configuration file.  

When I click on options 2 & 3 I get a blank window similar to a text editor but I can't enter anything.  However, option 1 gives me log file which is several hundred lines long, I have included a copy of the last ten or twelve lines which appear to be indicating what the error is, unfortunately I only have a rudimentary grasp of what it is telling me.

I have been to the Wiki ([http://wiki.x.org](http://wiki.x.org)) as advised, but that gave me one link which appears to assume I can access the boot manager on the machine, unfortunately as I have mentioned previously, I can't even get logged onto the machine nor can I get to the terminal. 

[[ Begining of snip ]]
[24.501] (EE) 33: /USR/BIN/X (InitOutput+0xadd) [0x7f553618d07d]
[24.501] (EE) 34: /USR/BIN/X (0x7f55360f7000+0x4437b)[0x7f553613b37b]
[24.501] (EE) 35: /lib/x86_64-linux-gnu/lib.so.6 (_libc_start_main+0xf5)
[0x7f5533e32de5]
[24.501] (EE) 36: /USR/BIN/X (0x7f55360f7000+0x448af) [0x7f553613b8af]
[24.501] (EE)
[24.501] (EE) Segmentation fault at address 0x8
[24.501] (EE)
Fatal Server Error:
[24.501] (EE) Caught signal 11 (Segmentation Fault). Server aborting
[24.501] (EE)
[24.502] (EE)
Please consult the X.Org Foundation Support at [http://wiki.x.org](http://wiki.x.org) for help
[24.502] (EE) Please also check the log file at "/var/log/Xorg.log" for additional information
[24.502] (EE)
[24.513] (EE) Server terminated with error (1). Closing log file.
End of snip]]  


Regards


Al

---

### Post by PopsTheSailor on 2014-01-13
Al,
unfortunately, I'm nowhere good enough to read these log files and make any sense of them. What version of the Live USB did you try? You might want to try 14.04 since it is the latest although it hasn't been released yet so it could be buggy.

Also, I've monkeyed around with Live USB sticks in the past and personally wasn't that successful with them. Do you have another computer that you could try booting off the USB just to make sure it is set up correctly? Sorry but I'm running out of ideas with my limited knowledge.

---

