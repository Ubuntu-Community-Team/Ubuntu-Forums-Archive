---
title: "Dell E1505 no wired no wireless with 9.10"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by 57erf89gh80ip on 2009-12-30
I installed Ubuntu 8.10 from a CD I'd made in August  onto my Dell laptop and had no wireless. But I moved it into the other room and connected the wire from the DSL and had wired access. I searched around the internet for hours for a solution to enabling the Broadcom 43 wireless hardware.

During the same hours I began the automatic upgrade to 9.10 but for some reason, after two-three hours of downloading and installing, it only made it to 9.04 and during that time wireless access became available whether through my efforts at the Terminal or something to do with the upgrade?

I switched to wireless, unplugging the DSL wire and returning it to my desktop, and began another upgrade, this time to 9.10. After another two-three hours the upgrade completed and upon reboot wireless was again disabled, but luckily the hardware driver application wanted to download a driver for it, so I plugged in the wire again, but I no longer had wired access either.

In desperation I typed in the web address shown on the "can't connect to" error message for downloading the Broadcom driver, downloaded something, put it on a thumb drive and moved the thumb drive to the laptop. I copied the file to the laptop and double clicked it. Something seemed to happen, but still no wireless access. 

I finished my day by loading Windows XP, deleting the Ubuntu partitions, and using my Windows XP disk to repair the MBR(?). I threw my Ubuntu 8.10 disk into the trash.

---

### Post by phillw on 2009-12-30
Hi and welcome to the Forums,

sorry you had problems.

Firstly, Broadcom are notorious for their * support* of any Linux. (Read as **lack of**)

For your System, for wireless it is this :

>                                   **Re: HOWTO: Dell Inspiron E1505 Wireless (Broadcom 1390 WLAN)**             
                                                                     Quote:
                                                                      Originally Posted by **sanemanmad**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6948594#post6948594")                 
                 [I]Hi ~ 

I wanted to post here and point out, that while all of you may now be able to use your wireless cards... you are circumventing Ubuntu's capabilities altogether. I just finished loading Hardy 8.04 on a lady friend's laptop (Dell Inspiron E1505 (Broadcom) ) and also experienced this same issue. Here are my details:

*Here the Wifi card is detected*
     Code:
     anna@anna-laptop:~$ lspci|grep -i network
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 
And if I try the network manager, I cannot see any networks. Yes, I verified the adapter was active using the keyboard functions.... (However, I still cannot see any networks.)

Now I try using the CLI...

     ```

     anna@anna-laptop:~$ iwlist eth1 scan
eth1      Interface doesn't support scanning. 
```as you can see I also am unable to choose from a list of wifi networks unless I manually enter in my settings (Which I have *not* attempted yet).

[COLOR=Black][SIZE=5]RESOLUTION[/SIZE][/COLOR]:

for me this was too easy....

     ```

     anna@anna-laptop:~$ sudo aptitude update && sudo aptitude safe-upgrade 
```*then*
     ```

     sudo apt-get -f install 
```*then*
     ```

     sudo apt-get install wifi-radar 
```That's all folks... Now if you goto the Network manager icon and choose the drop down, you should be able to list available networks in your area. 

Hope this helps and enjoy!


[COLOR=Red][SIZE=6]IN NO WAY DID I USE NDISWRAPPER AT ALL![/SIZE][/COLOR][/I]
                                 


So this worked for with one extra step, After installing wifi-radar, I had to got to System -> Administration -> Hardware Drivers and from there select the b43 driver and activate it. This got the WLAN status in Network Manager to 'Device not ready' After a reboot the wireless networks were detected. Eureka!

There is a quick rule that would have saved you so, so much grief - It's called "Try Ubuntu without changing my computer" - This allows you to see if things like audio, video and networking are going to "work out of the box", or if you need to ask a couple of questions.

The Dell computers have a seperate sub-forum, which you can find plenty of help at 
[http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

They're much more familiar with the intricacies of Dell computers & issues with them.

So, having the information to hand, you should find it a heck of a lot less painful this time.

Regards,

Phill.

---

