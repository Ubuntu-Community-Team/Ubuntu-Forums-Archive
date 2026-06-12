---
title: "computer won't boot after update"
date: 2016-04-12
forum: Installation &amp; Upgrades
---

### Post by Phil_Kushti on 2016-04-12
Hi,[br]1[/br]    I recently installed some updates on my computer running Ubuntu 14.04 LTS. After that the computer would not boot. I also could not access the GRUB boot loader. So I followed the advice on this page [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair):                   
[list=1]                
[*] I created a disk with Boot-Repair from [https://sourceforge.net/p/boot-repair-cd/home/Home/](https://sourceforge.net/p/boot-repair-cd/home/Home/)                  
[*] I booted the computer with the Boot-Repair disk and clicked on 'Recommended repair'                  
[*] After that I was able to access GRUB                 
[*] I clicked on 'recovery mode' and reached the recovery mode menu.                
[/list]
      However, none of the options in the recovery mode menu seemed to work. Boot-Repair created a report and pasted it to [https://paste.ubuntu.com/15660599/](https://paste.ubuntu.com/15660599/)   [br]1[/br] Help in solving this problem would be much appreciated. Please explain things in very basic terms - I am still a newbie re UNIX/Ubuntu.  [br]1[/br]  Cheers, Phil

---

### Post by Phil_Kushti on 2016-04-24
Would it be safe to try and reinstall Ubuntu? That is, would my documents survive the process?

---

### Post by Phil_Kushti on 2016-04-30
When I try to reinstall Ubuntu I get the option 'Install Ubuntu 14.04.1 LTS alongside Ubuntu 14.04.1 LTS. Documents, music, and other personal files will be kept. You can choose which operating system you want each time the computer starts up.' [br]1[/br] Is this normal? Should I not be able to simply reinstall it?

---

### Post by Bucky Ball on 2016-04-30
I'd stop what you're doing now if you haven't backed up any data you don't want to lose. It is normal but I wouldn't suggest simply installing without doing that first. Choosing that option would be installing a new install alongside the broken one. No point.

If you've backed up and don't mind losing everything on the disk by accident, go ahead. If not, boot from the installer and 'Try Ubuntu' then backup what you don't want to lose and try again.

You appear to have Windows installed on sdb1, which is odd. Please confirm.

Back to your original problem, when you say it won't boot after updates, can you be more specific? What's actually happening? Error message? More info helps us to help you. ;)

---

### Post by Phil_Kushti on 2016-04-30
> **Bucky Ball said:**
>  ...  You appear to have Windows installed on sdb1, which is odd. Please confirm.  Back to your original problem, when you say it won't boot after updates, can you be more specific? What's actually happening? Error message? More info helps us to help you. ;)    
 Thanks for your reply Bucky Ball. I don't have Windows installed on the affected computer.  

  When the problem started, all I would get was a BSOD. There was no error message. I could access the BIOS but not GRUB.  

  After I ran Boot-Repair I was able to access GRUB and reach the recovery mode menu. I tried out the various options but every time I got the following output on the screen:  [INDENT] fsck from util-linux 2.20.1 
                             /dev/sda5: clean, 313238/610800 files, 2096798/2441216 blocks [/INDENT]

---

