---
title: "Ubuntu 5.10 Live CD."
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by Alcwyn George on 2005-11-23
My live Cd does not load further than the brown screen...verbose... then blank.
  I have a partitioned HD Win 2000...Mandrake 9.2 
  Is this the problem?
                                 Puzzled.

---

### Post by aysiu on 2005-11-24
Bum disk?
Corrupted during download maybe?

---

### Post by Alcwyn George on 2005-11-24
Aysiu I tried two new copies [ they are not downloads I ordered them from Ubuntu/ Alcwyn.

---

### Post by dguido on 2005-11-24
There's no issue of compatability dual-booting Ubuntu with Windows 2000.  In fact, the install script auto detects windows partitions and adds correct boot menu entries for them in grub.  If you're afraid of getting a corrupt cd, then verify the md5sums with md5sum and instruct your cd burning program to verify its burn as well.

If Mandrake is booting fine, I would check to see if you're passing special options to your kernel to make it function properly and pass those to the Ubuntu installer.  My laptop for instance, needs to be started with acpi=off .

---

### Post by Alcwyn George on 2005-11-24
Is it because I have a dual boot Win 2000 / Mandrake 9.2 system the live CD will not instal further than the brown decktop verbose message setting disc parameters?

---

### Post by tseliot on 2005-11-24
EDIT: Oops, perhaps I misunderstood the thread

---

### Post by Alcwyn George on 2005-11-25
[QUOTE=dguido]There's no issue of compatability dual-booting Ubuntu with Windows 2000.  In fact, the install script auto detects windows partitions and adds correct boot menu entries for them in grub.  If you're afraid of getting a corrupt cd, then verify the md5sums with md5sum and instruct your cd burning program to verify its burn as well.

If Mandrake is booting fine, I would check to see if you're passing special options to your kernel to make it function properly and pass those to the Ubuntu installer.  My laptop for instance, needs to be started with acpi=off .[/QUOTE]

 I retried this time I used the Expert op mode and type as directed acpi=off.... then hit enter.
   It got as far as a blank desktop with a cursur that does not respond to the mouse. I hit Cntrl Alt Backspace message something second phase starting .....it stopped at 
 PCMCA not present. 
  Then I had to reboot by the RED button and remove CD.
                                          Alcwyn.

---

### Post by dguido on 2005-11-26
[QUOTE=Alcwyn George]I retried this time I used the Expert op mode and type as directed acpi=off.... then hit enter.
   It got as far as a blank desktop with a cursur that does not respond to the mouse. I hit Cntrl Alt Backspace message something second phase starting .....it stopped at 
 PCMCA not present. 
  Then I had to reboot by the RED button and remove CD.
                                          Alcwyn.[/QUOTE]

I didn't say to use acpi=off with your computer, I just offered up the suggestion of passing the kernel different options without specifying any exact solution.  There are pages full of different options you can pass your kernel.  Please reply with the make and model of your computer and maybe we can help you.  Also,  the xorg.conf and menu.lst from your mandrake partition.

---

### Post by tbcheese on 2005-11-26
I ordered 5 CDs and all 5 live CDs were unbalanced. They sounded like they were going to rip my drive apart. Apart from that they all work. First time trying linux and very amazed.

---

### Post by bwog on 2005-11-26
Ubuntu installation is designed to make install very easy, and you will see very few posts here by users who had no problem at all. In this section people come when they have problems, because there can be issues.

Point is that a poll in this section wont be representative, 

Even when there may be no fundamental problems with installation or with the live CD the poll will show too many users with problems.

---

### Post by dguido on 2005-11-26
[QUOTE=tbcheese]I ordered 5 CDs and all 5 live CDs were unbalanced. They sounded like they were going to rip my drive apart. Apart from that they all work. First time trying linux and very amazed.[/QUOTE]

seriously, it sounds like theres a problem with your computer.  get it checked out.  i doubt its ubuntu.

---

### Post by Alcwyn George on 2005-11-26
[QUOTE=dguido]I didn't say to use acpi=off with your computer, I just offered up the suggestion of passing the kernel different options without specifying any exact solution.  There are pages full of different options you can pass your kernel.  Please reply with the make and model of your computer and maybe we can help you.  Also,  the xorg.conf and menu.lst from your mandrake partition.[/QUOTE]
   
   I tried menu.lst    and xorg.conf  
  in mandrake and ...command not recognised!
   
  I tried expert Live CD install, and  got as far as a continuous turning circle on a blank screen ..then I did Ctrl Alt Back space...loading stopped at PCMCIA not present but this time Ctrl Alt Del did give me term and kill .
         My computer is generic one 350 mz AMD K6 C2 ... 30  gig HD 256 meg ram....logitech keyboard 2 urs old Daytek monitor 1 year old. A Open CD and CD burner less than two years old. Serial mouse 1 year old.
    I wanted to try Ubuntu first and if I got along with it replace my Mandrake with it because it's more upto date .
       Thanks for trying anyway, Alcwyn.

---

### Post by tbcheese on 2006-02-25
[QUOTE=dguido]seriously, it sounds like theres a problem with your computer.  get it checked out.  i doubt its ubuntu.[/QUOTE]

oops forgot all about my post here. anyway its not my drive. all other cds work fine

---

### Post by Alcwyn George on 2006-02-25
Problem solved. Deleted HD formatted and installed Ubuntu regular version, went slow but all was installed.
   Thank you all.

---

