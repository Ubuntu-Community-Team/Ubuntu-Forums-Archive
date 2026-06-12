---
title: "Ubuntu Live CD"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by opivy1218 on 2008-04-26
Hello, I am thinking of switching to Ubuntu, but first want to just demo it with a live CD. I know how to make the cd alreay, but what I'm unsure about is how to start it.
Do i just put the disk in and something will come up to boot it?
Also, after I'm done with it, do i just take the disk out and then i'll be able to start my current OS normally?
Any help would be greatly appreciated.

---

### Post by obidose on 2008-04-26
Stick the CD in, restart your computer.

Soon a menu will appear with instructions, you want the first option (something like run or install ubuntu without altering system).

When you are done select shutdown, before shutdown is completed you will be told to remove the disk, if you do so next time you reboot it will be as if you had never used the live cd.

---

### Post by Tatty on 2008-04-26
Put in the CD then reboot your machine.  Your bios should check you CD drive and see that it is bootable, so boot from there.

If it fails to do this then it is because it is set to check the hard drive before the CD drive.  You will need to go into your BIOS and change the boot priority so it checks the CD drive first.


After you shut down ubuntu it will tell you to remove the CD, then you can continue using your comp as if nothing had happened.  It will not make any changes to your hard drive unless you click the "install" button on the desktop - or unless you deliberately mount your hard drive and change things.

---

### Post by opivy1218 on 2008-04-26
ok thanks alot!

---

### Post by abstractcoder on 2008-04-26
You should place the cd into the drive. Let the computer load as usual, if you see "Press any key to boot from cd", hit any key and wait.

If your computer doesn't boot from the CD, you will have to enter your computer bios(setup screen). You can do this by hitting F1 or F2 when the computer is booting. Next, you will have to change the boot sequence, so that the computer boots from CD first. Instructions for changing the boot sequence will  be displayed. After, save and exit. Then place the cd into the drive again.

Once you successfully boot the liveCD, you can explore the operating system, and get use to everything. When you're finished, you can go to the menu on the top of the screen (system - quit), and choose to shutdown or restart. 

It will unload/shutdown everything that it loaded/started during booting. The cd will then pop out, you take the cd, close the drive and hit enter.

If you chose restart, your computer will now boot your regular operating system.

If you chose shutdown, your computer will shutdown, but load your regular operating system next time you turn it on.

---

### Post by ronald911 on 2008-04-27
I got my free disk of ubuntu 7.10 a while ago, but I would like to test it first like a demo, before downloading v8. I have never had a linux before. So which option should I chose to run 7.10, and not installing it?
I just want to test it first to see if I like it. I also dont want my pc modified at all.

---

### Post by juje on 2008-04-29
ok, i have a question about the live cd...im using happily using gusty and try to load the liveCD but fail to do it...i check the cd inegrity with md5 checksum and it's ok...i also try to load the gparted live cd and that one load quite good....any clue why only the hardy live cd not working? tahnks!

---

### Post by juje on 2008-05-02
ok, thanks everyone..i gave another shot to brasero and burn one new livecd (from other source) and it seems to work fine...

---

