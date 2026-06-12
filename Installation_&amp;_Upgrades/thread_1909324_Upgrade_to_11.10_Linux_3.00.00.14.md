---
title: "Upgrade to 11.10 Linux 3.00.00.14"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by IPEX-731BA5DD06 on 2012-01-15
I have a partial problem.

I've upgraded from 11.04 to 11.10

Linux version I'm currently running is this

[spoiler][IMG]http://i282.photobucket.com/albums/kk264/IPEX-731BA5DD06/Linux%20problems/Ubuntu1110Linuxversion2638-13.png[/IMG][/spoiler]

Trouble is, when I try to run 3.0.0-14 ( or what ever version it is close too) it has a kernel panic and just hangs.

I've tried to run the test version from BOTH  a CD and a USB stick. Both give the same kernel panic on initial loading.

How I arrived at this version, well it was partially luck I must admit.

I tried the normal upgrade, Linux version 3.0.0-14, was installed, I got a Grub selection of that version, my 10.04.3 LTS edition versions and 3rd line down, "Other versions of Linux".

Well, 3.0.0-14 was just hanging, both in normal and recovery mode. I clicked on "other linux versions" and eventually was loaded into this version of Linux.

This version is working fine under 11.10 ( I really wanted Unity again) but I'd like to get 3.0.0-14 working.

I do realize, these aren't meant to be LTS editions. That comes with 12.04.

Will I just have to wait till the linux kernel is updated for 2.6.38-13 to version 3.1.0-?? or is there some editing in Grub I can do.

Keep in mind I'm a Grade Newbie +1. I know enough to alter system, damage it, and repair it most times.

I've tried updating system, but none are available. So either I have most up to date kernel installed (booting or not) or I'm stuck at end of kernel upgrade line.

Any ideas appreciated, and maybe "Other linux versions" will help someone else.

---

### Post by IPEX-731BA5DD06 on 2012-01-16
SOLVED:

1st Problem definition:

I can't boot into kernel (insert kernel) It just hangs.

Solution Diagnosis:

1) Boot into Recovery mode, if you can fix it here, congratulations. I couldn't, it would still hang and spit out pages of text, but one common theme seemed to run acpi (this option, that option) would appear multiple time..Hmmm PROBLEM!!!!!

2) I did an Internet search on Kernel panic's and viewed this Youtube Video 

[COLOR=Lime][http://www.youtube.com/watch?v=jd9WIcPKc-o](http://www.youtube.com/watch?v=jd9WIcPKc-o)[/COLOR]

 Excellent video of solution 

3) If you have a live cd/usb. ( I used upgrade option from 11.04) Boot into that, at the Keyboard+man Icon at initial boot hit Esc. This takes you to options menu, F6 and select your problem fix. Me it was acpi was the problem, hitting return to give alternative option, enabled me to boot

4) As I used upgrade option from 11.04, I had to 1st edit the boot kernel line (hit Esc as per video) if you haven't watched, DO SO!!! I inserted acpi=off (3rd time, tried no acpi, acpi, watched video again, realized =OFF!!!!! Duh )

5) Try booting into kernel. Mine worked straight away, I'm using it NOW!!!

[IMG]http://i282.photobucket.com/albums/kk264/IPEX-731BA5DD06/Linux%20problems/Screenshotat2012-01-17100730.png[/IMG]

6) As per Video, 
Sudo gedit /etc/default/grub 
After "quiet splash" insert option required (mine was apci=off )
Save file. Update Grub, didn't work for me, still looking into that.
Update: AAARRGGGHHH MINUS.

sudo update-grub (AAARRRGGGHHHHHH MINUS IS NEEDED)

7) you now have fixed your kernel panic.

Thanks to Video author - Oleg ? You got it 100% Thankyou
Thanks to Ubuntu Authors/coders So easy to edit/fix

Remember, Boot into recovery mode, read the Text output. If you have a recurring item such as'
apci keyboard...
Blah blah couple of lines
apci usb
Blah blah couple more lines
apci processor 
Blah blah couple more lines
acpi..(you get the idea)

That's your error to fix.

Trial fix using the live cd/usb (so Good, I used a 12.04 alpha version with same problems to trial it out.)

Razor's Edge, HERE I COME

"Here comes the RAZOR'S EDGE...bah bah bam bah"...."Heeeere comes the RAZORS EDGE"....

---

### Post by IPEX-731BA5DD06 on 2012-02-17
More on this, I wasn't enabling the 2 processor cores I have with my system, only 1 was being enabled.

Solution:

Sudo edit /etc/default/grub add the following: noapic pci=assign-busses apcimaintainer idle=poll reboot=cold,hard

Update grub, reboot and you'll both processors enabled now.

---

