---
title: "installation hanging at &quot;Allocate drive space&quot;"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by deansy on 2011-04-25
Hi there, I am borrowing a friend's Eee PC 4G. Ubuntu eventually crashed  because the hard drive filled up (even after all personal files had  been removed). So now I'm trying to reinstall Ubuntu Netbook 10.10 from a  bootable USB. Creating the USB worked fine and I managed to get all the  way to the "Allocate drive space" screen. I opted to make no partitions  and just use the entire disk space for the install. It tells me that 2  partitions will be deleted, which is fine. I then click Forward and it  just hangs there endlessly, spinning its wheel. 

I suspect that  the already-full hard drive may be causing problems. Is there any way  around this so I can get the computer running again?

---

### Post by Hedgehog1 on 2011-04-25
**Please be sure that the user name is all lower case.**


If that is not the cause:


Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by deansy on 2011-04-25
Thanks Hedge, 

I haven't yet entered a user name so the caps issue isn't the cause

After clicking TRY, I tried to run the boot info script in a terminal; it tells me it is "Searching sdal for information..." but then doesn't do anything for a long time (>2hrs). When I shut down the terminal it tells me that there is still a process running but there seems to be no action. 

Any thoughts?

deansy

---

### Post by Hedgehog1 on 2011-04-25
Please run and post the script output as requested above.

You may have all 4 primary partitions already allocated, or some other situation.  The output of this script give us in insight into your soul - urrr - I mean your drive(s) and partitions(s).


***The Hedge***

:KS

---

### Post by deansy on 2011-04-25
I set the script running but it has not returned any results, even after leaving it overnight. I've tried it several times with a few variations, but no success. 
 
deansy

---

### Post by Quackers on 2011-04-25
The boot script takes about 3 seconds to run. It produces a file called Results.txt in the same directory as the script. 
Where did you download the script to?

---

### Post by deansy on 2011-04-25
The script came to Downloads, so I ran it with the command: 
 
```
sudo bash ~/Downloads/boot_info_script*.sh
```
 
It seemed to run the script, i.e. told me it was searching for information, but no result.

---

### Post by Quackers on 2011-04-25
And in the Downloads folder there is no file called Results.txt? That's odd. Not good.

---

### Post by deansy on 2011-04-25
No, nothing turned up. I'll double check when I get home but no sign of a Results.txt file when I last looked.

---

### Post by Quackers on 2011-04-25
Ok check that please.
Also start the Disk Utility program and see if anything untoward is reported for your hard drive and check the SMART status.
Also please see what gparted reports for your hard drive structure (partitions-wise), if anything.

---

### Post by deansy on 2011-04-26
Definitely no Results.txt file. 

Gparted screenshot attached. The disk utility doesn't report any problems for the hard drive. However, before the netbook crashed there were constant messages of the hard drive being used outside the design parameters (probably should have done something then :).

I did notice the option in the disk utility to format the hard drive and I'm wondering if this is worth a shot before installing Ubuntu from the USB.

deansy

---

### Post by Hedgehog1 on 2011-04-26
Thanks for the gparted screen shot.

I work with massive drives, I forget that some folks work at the other end of the spectrum and still get the job done.

According to the 'Unused' column, you have less the 200 megs of 'disk/SD' space left.

**Did you empty the 'trash' after deleting the data?**

When you installed Ubuntu again, did you format the /dev/sda1 to start fresh? This might explain why you have no space left after the install.  



**Other Thoughts:**
Does this notebook allow for a second SD?  If so you could make that the '/home' partition and split up OS and User Data.  I just saw an 4 gig SD card in the checkout line at the grocery store for 10 dollars.

If you can add a second SD card, here is the basic concept of joining them into a single file system:

[IMG]http://img863.imageshack.us/img863/6315/netbooksd.png[/IMG]


***The Hedge***

:KS

---

