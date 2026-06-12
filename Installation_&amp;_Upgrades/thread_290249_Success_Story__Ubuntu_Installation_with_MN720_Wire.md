---
title: "Success Story : Ubuntu Installation with MN720 Wireless network on Compaq 1830"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by dashingdon on 2006-11-01
Success Story : Ubuntu 6.06 LTS Installation with MN720 Wireless network on Compaq 1830 [Apologize for long post]

Being a windows user for 10+ years I am very comfortable (?) applying all the patches , installation of antispyware(s) , antivirus(s) and firewall(s). So last Sunday (10/29/06) , a very fine morning  I started starring at my wife's Compaq Presario 1830 , PIII , 192MB RAM with an itch of installing UBUNTU. As she only uses this machine for browsing, I did not needed any more reason, NOT to install LINUX. Ubuntu was the first choice as I already had played with 5.10 on the vmware environment. But this was going to be the first install on REAL hardware.

All psyched up with the thought, at 10.00 AM I started my "Other" computer, downloaded 6.10 Edgy EFT ISO , burned the CD and popped into Compaq. Rebooted and there comes a live desktop. Happy and all, clicked on INSTALL hoping to show "something" which will start the install process. Alas.. Waited for at least hour, nothing showed up and computer was frozen, Rebooted and repeated process 3-4 times only with the exception of not waiting for too long. Result was exactly same as initial try. Meanwhile I kept reading the forums for possible solutions.

Disappointed, but now I downloaded 6.06 LTS dapper, repeated same process as above. Rebooted and Live desktop comes up, clicked on Install, After waiting for 20 mins or so ..Hurray.. I got the installation Wizard Step 1 0f 6 , Select Language window. Clicked "Forward". Step 2 , Select Time Zone window opens up. At this point, Cursor kept spinning for ~30 mins , I was not even able to open the dropdown to select "Time Zone". Hard rebooted, repeated process couple of times with same output. 

Again At ~4.00 PM , I downloaded 5.10 , repeated the process and YES , installation process started successfully. I was so happy at this point in time, I took a coffee break and let the installation run for hour or so only to find that the process was frozen at 25% while copying packages to Hard Drive.

now extremely frustrated I still kept telling myself , Linux is all about Patience even if it is Ubuntu with the most user friendly installation process. I restarted again with ONLY difference of, while formatting the drive I formatted with LVM. 

AND YES... Finally my installation went very smooth. Ubuntu 5.10 even detected my USB mouse and D-Link DFE-690TXD network card. My Ubuntu was up and running, connected to the internet at 6.30 PM. 

Now the next step was to upgrade 6.06 dapper. Performed the search again and found this blog ..

[http://daniel.holba.ch/blog/?p=14](http://daniel.holba.ch/blog/?p=14)   

This is the "Best" step by step "Working Guide"  (at least for me) . Followed every single instruction and finished the upgrade ~10.30 PM. I was very happy camper by now with EVERYTHING working including wired network.

Next immediate step was to configure my Microsoft MN720 wireless card. Just for the information , I have this card since last 3 years , used it on Microsoft OS's without any issues. So with confidence , I searched the forums again :-k   

Here are the steps I took to configure MN720

Download Latest Ndiswrapper : [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

Download Ankh Driver for MN720 : [http://ankhcraft.com/drivers/mn720-ankh.zip](http://ankhcraft.com/drivers/mn720-ankh.zip)

Follow below thread step by step. If having issues with "Make Install" , perform in the terminal window "Sudo apt-get install build-essential". Get the latest Linux Kernel. Used Synaptic (Easier). 

[Make sure to replace and use YOUR version of Ndiswrapper and Linux Kernel and DO NOT INSERT WIRELESS CARD UNITILL STEP 5] 

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

I followed the process as above and was successfully able to install MN720. My Power lights and everything was working fine. I was able to browse until the reboot. As soon as I performed reboot , My card was equal to dead. No lights at all but "Sudo Ndiswrapper -l"  was showing all correct information. I must mention here that during the wireless card installation process, "Sudo Ndiswrapper -m" FAILED. May be that the reason why my card lights were not started.

So that closes the sunday work at ~1:30 AM. Went to sleep. Again on Monday , after office hours ~7.00 PM , Here we go again , back to the forum search. Tried following thread suggestion but I already had RadioState = 0 [This is the file path to check RadioState : /etc/ndiswrapper/mn720-ankh/14E4:4325.conf ]

[http://ubuntuforums.org/showthread.php?t=64366](http://ubuntuforums.org/showthread.php?t=64366)

Then I stumbled upon this thread ..

[http://ubuntuforums.org/showthread.php?t=283696](http://ubuntuforums.org/showthread.php?t=283696)

Issue seemed to be related to blacklist of 'bcm43xx'. So I applied this (again from the above thread)

*************************************************
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

*************************************************

And my card started working :) Rebooted and again lost the card :(  What the hell... ](*,) 

So I ended up adding following to my /etc/rc.local before "exit 0" (Here is reference Thread for rc.local: [http://ubuntuforums.org/showthread.php?t=286958](http://ubuntuforums.org/showthread.php?t=286958))

*************************************************
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo iwconfig wlan0 essid name_of_AP (the name you found by using iwlist wlan0 scan) 
iwconfig wlan0 enc <key> (fill out your WEP key (if you have one)) 
sudo dhclient wlan0 (gets a dynamic IP address) 

*************************************************

Now I can reboot the machine as many times or pull my card and Insert back , It is recognized and connected to internet in few seconds. :):) Monday 10.00 PM , I was finally browsing internet on my Ubuntu :mrgreen: :mrgreen: 

Don't think, I am going to upgrade 6.10 sooner as 6.06 will serve the purpose unless there is a SOLID reason.

Still have a lot to learn about Ubuntu and Linux overall BUT I am definitely happy that I no longer have to maintain Patches / Spywares etc to remain safe. I still installed CLAMAV antivirus just to have some peace of mind but I am aware that one don’t need to install antivirus on UBUNTU DESKTOP
 
Hope my experience will help newbie’s like me to get over with the  frustration of Linux Installation and hope for the best from UBUNTU. 

UBUNTU ROCKS !!!!!!!!
 
[Just for Reference, Here is the list of all network drivers compatible with Ndiswrapper -- [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List])

---

