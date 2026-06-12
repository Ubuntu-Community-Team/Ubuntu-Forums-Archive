---
title: "Reported Problems 10.04 LTS 2.6.32.38 Read before updating!"
date: 2012-01-26
forum: Installation &amp; Upgrades
---

### Post by JoeFriday49 on 2012-01-26
Updating from 2.6.32.37 to 2.6.32.38 will break your Realtek wifi drivers and reinstalling drivers won't make it work.  
See this thread: [https://bugs.launchpad.net/ubuntu/+bug/921141](https://bugs.launchpad.net/ubuntu/+bug/921141)
And this: [http://ubuntuforums.org/showpost.php?p=11640098&postcount=1](http://ubuntuforums.org/showpost.php?p=11640098&postcount=1)

There is currently no solution, and I haven't tested with other wifi cards...  Booting back to 2.6.32.37 will allow the system to be used until this can be resolved.

---

### Post by malangaman on 2012-01-26
Thanks for the heads up.

---

### Post by JoeFriday49 on 2012-01-31
> **JoeFriday49 said:**
> Updating from 2.6.32.37 to 2.6.32.38 will break your Realtek wifi drivers and reinstalling drivers won't make it work.  
See this thread: [https://bugs.launchpad.net/ubuntu/+bug/921141](https://bugs.launchpad.net/ubuntu/+bug/921141)
And this: [http://ubuntuforums.org/showpost.php?p=11640098&postcount=1](http://ubuntuforums.org/showpost.php?p=11640098&postcount=1)

There is currently no solution, and I haven't tested with other wifi cards...  Booting back to 2.6.32.37 will allow the system to be used until this can be resolved.

This Bug has been marked as confirmed, but is still unassigned...  

Can anyone tell me if it's safe to update the other 2 systems that I have also running 10.04 that don't use this particular card?

---

### Post by JoeFriday49 on 2012-02-03
> **JoeFriday49 said:**
> 
Can anyone tell me if it's safe to update the other 2 systems that I have also running 10.04 that don't use this particular card?

Another user posted to the bug report with the same problem, but they are using the same chipset I am.  Still don't know if it's safe to update the other machines I have that are running 10.04 LTS

---

### Post by JoeFriday49 on 2012-02-08
Still not assigned and without resolution...  Is anyone using this build without problems with other chipsets?

---

### Post by Linuxer on 2012-02-08
I lost my wireless as well with 2.6.32.38, .37, and .36.  2.6.32.35 works fine.  How can I safely remove 2.6.32.38, .37, and .36?

Thanks in advance.

Linuxer.

---

### Post by JoeFriday49 on 2012-02-08
> **Linuxer said:**
> I lost my wireless as well with 2.6.32.38, .37, and .36.  2.6.32.35 works fine.  How can I safely remove 2.6.32.38, .37, and .36?


There will be periodic updates and we will have no idea which ones will work.  My system worked fine up until I installed this latest "38" release... My update preferences are set to only install Important security and Recommended with the pre-release and unsupported updates turned off...   I just wonder if "39" will fix it...  

I have another laptop and 2 desktops that I'm afraid to allow to upgrade and I know there are some security issues in with the update package.  Can't help but feel vulnerable to whatever security issues were patched.  

The bug report I linked to in the first post is still unassigned, but it only mentions the one wifi chipset that is affected, so it may not warrent the time required to fix it...  I just wish i knew what other chipsets that may be affected.

To answer your question, I don't know how to safely remove the updates, or whether when and if a working update comes out they will be required to be installed in order to update.

---

### Post by Linuxer on 2012-02-09
Thanks for your response.  Incidentally, my problem occurred on a Lenovo G450 laptop.  It has a Broadcom wi-fi chip.

Linuxer

---

### Post by JoeFriday49 on 2012-02-10
> **Linuxer said:**
> Thanks for your response.  Incidentally, my problem occurred on a Lenovo G450 laptop.  It has a Broadcom wi-fi chip.

Linuxer

If you haven't already, post your problem in the folder "Networking & Wireless"  It will get more attention there...  You need to include the outputs from the following querries in your initial post (Copied from sticky):


<snip>
 				 				**HOWTO post a Wireless issue (ticket)** 			
 			 			 		   		 		 		Please take a while for the **title**  of the thread. Do not write things like "Help wireless" and "Can't  wireless". Think a little bit more, a good title can increase the  chances to get help. For instance, add the **Wireless brand**/**Ubuntu version**/**Machine Brand and Model**.

Please, provide details about you Wireless. The diagnoses of your problem can be easer and the solution faster.

Here is a list of Wireless related information with their respective  commands. Some commands give you a lot of output, so will be nice to  include in the post only the information regarding the Wireless. You can  cut it or use tools like **grep**, or whatever you like.

**1 ) Machine Brand and Model (PC/Laptop)**:
 	Code:
 	Get it from your product information. 
**2 ) Wireless Brand, Model and Wireless Chipset:**
 	Code:
 	$ lspci
$ lsusb 
([COLOR=Red]hint[/COLOR]) use **grep** to get only information about the Wireless
 	Code:
 	$ lspci -nn | grep 'Wireless Brand' 
**3 ) check interface:**
 	Code:
 	$ ifconfig
$ iwconfig 
([COLOR=Red]hint[/COLOR]) if the Wireless interface name is wlan0 you can also use
 	Code:
 	$ iwconfig wlan0 
**4 ) Check for modules:**
 	Code:
 	$ lsmod 
([COLOR=Red]hint[/COLOR]) search for the Wireless module
 	Code:
 	$ lsmod | grep "wlan_module_name" 
**5 ) Kernel boot messages**
 	Code:
 	$ dmesg 
([COLOR=Red]hint[/COLOR]) the same as in (4)

**6 ) Network configuration**
 	Code:
 	$ sudo lshw -C network 
**7 ) Scan for networks:**
 	Code:
 	$ iwlist scan 
([COLOR=Red]hint[/COLOR]) the same as in (3)
 	Code:
 	$ iwlist scan wlan0 
**8 ) Ubuntu Version: **
 	Code:
 	$ lsb_release -d 
**9 ) Kernel/architecture (including 32 vs. 64 bit): **
 	Code:
 	$ uname -mr 
**10 ) Restarting the network:**
 	Code:
 	$ sudo /etc/init.d/networking restart 
Add this information to the post, even is the output is and error, and more if you have, and describe your issue.
 		                   		  		  		 		 			 				__________________
				Best,  Gnusci

---

### Post by JoeFriday49 on 2012-03-03
No movement on bug report.

---

### Post by JoeFriday49 on 2012-04-23
Just tested kernel 2.6.32-41...  Bug still exists in this latest release.

---

### Post by JoeFriday49 on 2012-06-13
Today was the 3rd time I received a notification to upgrade to release  .41...   I don't understand this.  It is a 41 MB download, and has been  each time I've installed it.  Regardless of how many times it wants to  download, it still doesn't work on wifi, and now has broken the  notification applet...  Back to good ole release .37...  It's still  fine...

---

### Post by dino99 on 2012-06-13
where is the bug report about that issue ?:confused:

---

### Post by JoeFriday49 on 2012-06-13
> **dino99 said:**
> where is the bug report about that issue ?:confused:

It's in post number 1...
[https://bugs.launchpad.net/ubuntu/+bug/921141](https://bugs.launchpad.net/ubuntu/+bug/921141)

---

### Post by JoeFriday49 on 2012-06-29
Today's latest image did not fix this wifi problem...

---

