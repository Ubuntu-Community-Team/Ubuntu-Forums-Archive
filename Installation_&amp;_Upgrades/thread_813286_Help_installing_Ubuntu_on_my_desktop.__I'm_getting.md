---
title: "Help installing Ubuntu on my desktop.  I'm getting some sort of hard disk error"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by geefunk on 2008-05-30
Hi
I'm new to this site, new to Linux, and a beginner when it comes to computer stuff but I'm not completely useless.
I'm trying to install Ubuntu on my desktop and I get an error every time I do it.  I cannot remember exactly what the error message reads but it goes something like "Cannot find the ata hard disk"
This doesn't just happen with Ubuntu; I get the similar error message when I tried Fedora, Debian, and Mandrake.

To anyone who is willing to try and help me out:
I have no idea what info you guru's would need to help me but if you tell me how to get the info I will give it to you.
Hopefully this is a good starting point...
My machine is a HP Media Center PCm7170n.  I have made no significant changes to it from when I bought it (other than a new hard disk and a 2 gigs of mem) so if you check the HP site you'll be able to find out what my hardware looks like.
System Information:
Windows XP Pro
5.1.2600 service pack 2 build 2600
x86 based pc
Intel Pentium D

As I said before, I am not an advance computer user but I think the problem might have something to do with this....
My computer's hardware seems to be set up in such a way that the cd roms operate off of (p)ata configurations and my hard disks operate off of sata configurations.  I think when the installation is doing its thing it gets confused since I'm installing/booting from my (p)ata cd rom and it things my whole system is (p)ata...which is why I get that error about not being able to find my hard disk (which is sata).  I may be way off base with my hypothesis though.

I apologize if I'm being to vague with my description.  If anyone is willing to help me I can try and provide you with any other information you might need.

Thanks for you time and I look forward to joining this community and exploring/learning about Linux.  I'm already loving it!!
P.S. I have successfully installed Ubuntu on a previous machine I owned and it worked without a hitch.  But I don't wanna run it off of just that old machine.  I want to have it on my current machine also.
Thank you for your time

---

### Post by Pumalite on 2008-05-30
Edit the boot line (hit F6); add all_generic_ide at the end of the line. You might need some other boot parameters. Post back if you need to.

---

### Post by geefunk on 2008-05-30
WOW...thank you for your prompt reply!
I wasn't quite sure what you were trying to say but I googled it so I could clarify a few things and I'm happy to say it seems to have worked just fine.
I'm in the middle of the install right now.
Just one more question...
While I was reading up on this problem I noticed that other people with this problem were talking about "making the change permanent"  Is that something I'm going to need to do after I finish installing?  And if so, am I going to have to go to /boot/grub and add the changes to the menu.lst?

---

### Post by Pumalite on 2008-05-30
Edit /etc/menu.lst (back it up first) and add it to the kernel line.

---

### Post by geefunk on 2008-05-30
Again, thank you for getting back so quickly!
I think it might have automatically made the change permanent for me.  After I installed the OS it booted from the hard disk just fine and I didn't have to do anything.  I'm actually replying to you on Ubuntu right now; it's running the update manager and everything seems to be just fine.
Will it be ok to just leave the menu.lst alone or is it going to cause some sort of problem down the line?

---

### Post by Pumalite on 2008-05-30
You can't beat success!. Leave menu.lst alone. Glad you got it working.

---

### Post by geefunk on 2008-05-30
Thanks
I really appreciate your help.  Too bad the world doesn't have more people like you guys.
I just have one more question for you then you're all done with me...
What was the problem??  Was the problem caused by the combined ata sata configuration of the hardware??  Or was it something else that was completely above my head and I didn't even realize??

And thank you again.  I was trying to figure this thing out for 2 days and you managed to get me up and running in under 2 hours.

---

### Post by Pumalite on 2008-05-30
It was probably your mix of ATA and SATA devices. Have fun!

---

