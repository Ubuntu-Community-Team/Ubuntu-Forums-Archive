---
title: "Can't boot 10.04 beta 2"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Pressondude on 2010-04-13
I was forced to install using the alternate disk, and upon successful install, I cannot boot up. I get to the splash screen, but after it gets to the point where the xserver should start up and I should see my login screen, my monitors go black and say that I've lost input. This is also what happened when I tried to initialize the standard installation disk.

---

### Post by superkabii on 2010-04-13
Mine did this too (and still does)
What I have to  do is on the boot screen where it says the company name (DELL in my case,) you have to open the boot menu
It might be F12 to open it
I then have to go down to Hard Disk C:/ and hit enter,
then my Ubuntu boots correctly, but Kubunutu is probably the same

---

### Post by Pressondude on 2010-04-13
I'm dual booting. I would still initialize through the GRUB. Also, I'm using a custom built system, not a Dell.

---

### Post by overdrank on 2010-04-13
Moved to  Lucid Lynx Testing and Discussion :)

---

### Post by Pressondude on 2010-04-14
Would it also be pertinent to mention that I also had this problem with the Beta 1 disk/install. I also had this problem with the standard install disks as far back as 9.04 (using GNOME)

---

### Post by ronparent on 2010-04-14
I've had the same problem with my newest build and was't sucessfully able to boot it until last week. Now am in the process of trying to install on a raid0 drive (another story).

To sumarize my findings with my unit:

The live cd and installed system both lock up and require a hard reset to retry booting. The fixes for me: 1)I can eventually boot with a nodmraid parameter on the kernal command line. This I have needed whether or no I have theraid configured in bios. 2) I've had to unplug a second monitor for booting to proceed. Suposedly this will not be required once 10.04 is installed - I haven't yet tested. 3) I've had to remove the splash parameter from the kernel command line. 

In addition, depending on how your bios has been implemented, you might also have to use the noapic nolapic boot parameters - I've had to use them on earlier AMD 64 builds but not on my latest including an AMD Athelon 64 X2 hp laptop. I hope this gives you a starting point. Post again if this work for you or you need more help. I can give you more explicit instruction for modifying the boot line if you need.

---

### Post by Yarrgh on 2010-04-14
I also had this problem. I tried to do a fresh install with beta 2 and it wouldn't and completely stopped when it should've moved on exactly as you pointed out (except mine doesn't go black). What I did was push F6 while booting into the live disk and selected nomodeset. Then I continued to boot into it, which succeeded. Unfortunately after you install the same problem still exists. But when you get to the ubuntu boot screen (or slightly before) hold or keep pressing F6 until it boots correctly. On my machine this caused the theme to look all ugly. I then updated to the latest changes and installed the proprietary driver. I know can boot successfully without holding F6. But now the boot screen is zoomed in too close and looks ugly. But after I get past that screen everything else looks fine.

---

### Post by Pressondude on 2010-04-15
Well this sounds like fun. Does this seem like a problem that will be fixed when the full version is released? Or should I just clench my teeth and go for the beta 2 install?

---

### Post by ronparent on 2010-04-15
I don't think the fake raid (dmraid problem will be fixed. But unless you are using raid (and it doesn't sound like you are) then you won't be affected as far as being able to run is concerned.

To be able to boot you would have to find the command line parameters that will work for you. This is a trial and error process and requires patience but is otherwise straight forward. 

It involves ading or removing combinations of the line parameters "noapic nolapic, nodmraid nomodeset quiet splash" until the system boots. The odds are that considering your build all will be probably needed except quiet (which should be removed during trial to get a clue to where your boot process stops). The edits made on the grub menu kernel command line are tempoary only for that boot. To make them permanent you have to edit the default grub configuration file (I'll have to look it up if you are interested because I am not currently writing from lucid). It sounds like a lot of trouble but once done the changes made should carry over and work on the final release. As a matter of fact you can probably expect only the splash parameter to be probably fixed. Other than the need to modify the splash and dmraid parameters it does'nt appear that the need to enter these command line parameters is considered a bug.

---

### Post by Pressondude on 2010-04-15
Oh that does sound painful. How exactly does one edit the boot parameters? Sorry to be a n00b, but my computer expertise disintegrates once I lose GUI, and I'm a total n00b at the kernel level. Not exactly something that I've ever had to do before.

---

### Post by ronparent on 2010-04-15
I feel your pain. I have had to assimulate some non gui skills to barely survive (like a monkey copying keyboard commands).:)

But to get to the issue. I assume your grub menu shows during booting. If not you can get it to show by holing down the left shift after bios. Hit 'e' at your boot line to edit the boot sequence. Move the cursor to the kernal boot line and hit <end> to move the cursor to the end of the line. Use the backspace to eliminate splash ans quiet. Just type in the boot parameters I mentioned. Hit <ctrl>x to boot. You might as well start out with all of the parameters I mentioned. When it boots, you have a combination that works. Then if you want to make whatever parameters that work permanent, you can add or remove parameters from the boot line by editing the file **/etc/default/grub** (it should be the line with boot splash already present  - ie in a termial window type **sudo gedit /etc/default/grub**). 

Let me know how you make out.

---

