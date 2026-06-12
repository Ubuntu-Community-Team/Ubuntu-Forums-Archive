---
title: "dual boot using boot partition"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by Xploit on 2007-09-01
Alright this afternoon I installed kubuntu and got grub error 18.  I realized I had a old BIOS so reformatted my drive and made a seperate /boot partition.  After that everything worked properly.

Later on in the evening I saw ubuntu ultimate so I wanted to give that a try, I installed that on the remaing 70 gigs of space on my drive and next thing I know I'm getting grub error 17.  I kinda knew what was happening since I put all the boot stuff right in the / partiton of ubuntu ultimate.

So I bit the bullet and reformatted again by formatting my /boot partition and using that for ubuntu ultimate.  Well obviously after the format of /boot everything related to kubuntu boot was lost.

How can I have my kubuntu kernel and ubuntu ultimate kernel in the same boot partition, since during install it always mandates you to format the boot partiton.  Since they are both Fiesty Fawn is it possible to use the same kernel for both distros?

---

### Post by Herman on 2007-09-02
>  How can I have my kubuntu kernel and ubuntu ultimate kernel in the same boot partition, since during install it always mandates you to format the boot partiton. Since they are both Fiesty Fawn is it possible to use the same kernel for both distros?    	 	 	 	 	    			 	    
Hello Xploit,
Try reading this thread, especially the second page and see if that sounds something like what you want to do, [two linux, same /boot  ]("http://ubuntuforums.org/showthread.php?t=364368&highlight=herman"):)

Regards, Herman :)

---

