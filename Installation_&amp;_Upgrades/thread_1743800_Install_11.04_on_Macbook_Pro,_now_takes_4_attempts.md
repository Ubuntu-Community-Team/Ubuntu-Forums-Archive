---
title: "Install 11.04 on Macbook Pro, now takes 4 attempts to boot, and beeps on restart"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by biot023@gmail.com on 2011-04-29
Hi -- I've tried to install 11.04 on my Macbook Pro (5,4) today.
I had two drives in the machine, an SSD as my main drive, and an HD.
I installed rEFIt before attempting to install Ubuntu.
I moved my Snow Leopard install to the secondary HD & made sure I could boot to it.
Then, I used the live CD & gparted to clear the 1st drive (the SSD), create the swap space, create the Ubuntu partition, and launch the install, where I used what I had just created on the SSD.
The install completed okay (but with no option to select where the GRUB installer went, like some tutorials tell you to look out for).
This seemed to go okay, so I went to restart at the end of the install, but the machine didn't come back up.
Instead, the power came on & I could hear the drives, but the screen stayed black, the battery light flashed a load of times really quickly (too quickly to count, but at least 10 times), and then the machine let out 1 long beep and stayed on the black screen.
I forced it to power down & tried again, and just got a black screen, the battery light shining steadily, and no beep.
I forced it to power down again, and got the same, then again, and got the same, and then a 4th time, which actually allowed me to boot.
And this has been the pattern since then. I shut down, and my first attempt to restart gets me the flashing light and the beep, with the black screen. I try 3 more times to power down and restart, and just get the black screen. Then, *every* time on the 4th time, I'm allowed to boot.
The same routine will be gone through the next time I power down and try to restart.
I've tried totally clearing the disk in gparted, restoring the OSX install from TimeMachine, everything I could think of, but all to no avail.
Finally, thinking that maybe the OSX install I had safe on the secondary HD might still be okay (looking at it in gparted showed an EFI boot section & everything), I opened up my MBP, swapped the drives around so that the HD is now the main drive, and the SSD the secondary, and renamed the drives so that the primary HD is now called 'Macintosh HD' and is first in the list of drives that appear when I manage to boot each 4th attempt.
But, to my great disappointment, I still got exactly the same error.
Can anyone offer any advice on how to:
  1) Get my machine booting to a safe Snow Leopard install on the (now primary) HD?
  2) Safely install Ubuntu on the (now secondary) SSD?
Obviously the first is a top priority, as I need my machine in order to work!
Then I can concentrate on moving my dev environment to Ubuntu, which I've been dying to do for ages.
Thanks very much for any & all assistance,
   Doug.

---

### Post by bademeister on 2011-04-30
Hello Doug,

I have the exact same issue as you, although I am comming from a slightly different setup -- I have a MacOS Partition, and two ext4 partitions (one for / one for /home) on the same harddisk.

I am seeing the exact same pattern - three or four times a black screen (although sometimes I will get a flashing light and a long beep, I think this is after I have booted into mac os), and then one reboot where everything seems to work.

Have you filed a bug report? If not I will.

Kind regards
Paul

---

### Post by bademeister on 2011-04-30
Here the link to the bug report:

[https://bugs.launchpad.net/ubuntu/+bug/774089]("https://bugs.launchpad.net/ubuntu/+bug/774089")

---

### Post by biot023@gmail.com on 2011-04-30
I haven't, and am out on department store duty with my Mum all day, so if you could report it, that would be great.
Good to know I'm not alone, although bad luck for you!
   Doug.

---

### Post by Who on 2011-05-01
I also have this problem; Apple are recommending a logic board upgrade - which isn't great news! I've written all the details on that bug report, which is the best place to keep things.

biot023: It looks like you haven't got rid of your logs yet - they would be extremely useful for the bug report. Specifically the developers want /var/log/installer/syslog, /var/log/installer/partman, and possibly /var/log/installer/debug 

The chances of getting a good clean fix that doesn't involve hardware replacement are much increased by giving accurate information to the developers and so logs are the best chance people have right now! 

**So, if anyone else has this problem, PLEASE save your logs**
Who

---

### Post by bademeister on 2011-05-01
Doug,

not sure if you are following the bug report, but somebody found a post which details a solution (reflash your efi with a secret command...) and that solution has been working for most of us, so you might want to give it a shot.

Bug report (solution in post #17):
[https://bugs.launchpad.net/ubuntu/+bug/774089/comments/17](https://bugs.launchpad.net/ubuntu/+bug/774089/comments/17)

The solution is found here (It is for a macbook pro 5,1 but with the appropriate firmware I was able to get it to work with my macbook pro 5,5)
[http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/](http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/)

Best of luck
Paul

---

### Post by goleary on 2011-05-24
I have a MacBook Pro as well and I would like to dual boot with ubuntu, but I am warry of flashing my EFI because I can't find the firmware for my exact version on the apple website.  There is 5,3 and 5,5 but no 5,4.  I just do not want to brick my device, so to the OP did this fix work for you as well?

---

