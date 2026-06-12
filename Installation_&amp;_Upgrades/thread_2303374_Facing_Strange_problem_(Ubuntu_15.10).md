---
title: "Facing Strange problem (Ubuntu 15.10)"
date: 2015-11-18
forum: Installation &amp; Upgrades
---

### Post by Kinshuk_Lahiri on 2015-11-18
Hello,

I am using a HP laptop and my system is running on both Ubuntu and Windows 10. So, I have been on Ubuntu 15.04 and everything was good and today I upgraded to 15.10 and the end of the installation it asked to restart and I restarted and then normally selected ubuntu and logged into the system and everything was good and then I shut down the laptop and went for some work. 

And I returned and started the laptop and selected ubuntu from the boot loader option and it showed the ubuntu logo and the dots remained white and none of the dots went orange and the screen was frozen. Then I have to force-shutdown the laptop by holding the power off button. And then when I again powered on the laptop then the screen remain black and nothing was working. As I just tapped the power button (didn't force to shut down) it automatically shutoff.

And then I kept on trying and nothing worked. And then I removed the battery and then turned on and then booted to Windows and everything was fine. So I shut down the laptop and started the laptop again and selected Ubuntu and again the screen froze and the dots remain white and again I pressed the power button to shutdown the laptop. After that, I again pressed the power button to start the laptop and the same problem appeared. Black screen nothing was working. And then I popped out the battery again and then it worked.

 So can anyone tell me how to solve this problem. I am completely new to Ubuntu FYI.

Thanks.

---

### Post by Bucky Ball on 2015-11-18
*Thread moved to **Installation & Upgrades**.*

Welcome. To improve your chances of support, please try adding some paragraphs. 'Wall of text' posts tend to be less effective. :)

---

### Post by Kinshuk_Lahiri on 2015-11-18
I will keep it in mind. Can you please provide some help regarding this problem?

---

### Post by grahammechanical on 2015-11-18
How long did you wait before powering off the laptop? Does the laptop have an LED that indicates if the hard disk is being accessed. Was the hard disk being accessed with only the screen not showing any activity?

I find that if I use a proprietary video driver I do not get the purple screen with the dots. But If I use the open source video driver I do get the purple splash screen. And that is really all it is, a splash screen to hide any Linux system messages that might be confusing to the user. If there is hard disk activity then I know the system is still loading.

It is possible, that all this powering off has disturbed the loading profile. You can try using Advanced Options for Ubuntu from the boot menu to select Recovery Mode and then Resume. See if that gets you to a working desktop.

Also, you might wish to use Recovery Mode>fsck to check all file systems - partitions

Regards.

---

### Post by Kinshuk_Lahiri on 2015-11-18
> **grahammechanical said:**
> How long did you wait before powering off the laptop? Does the laptop have an LED that indicates if the hard disk is being accessed. Was the hard disk being accessed with only the screen not showing any activity?

I find that if I use a proprietary video driver I do not get the purple screen with the dots. But If I use the open source video driver I do get the purple splash screen. And that is really all it is, a splash screen to hide any Linux system messages that might be confusing to the user. If there is hard disk activity then I know the system is still loading.

It is possible, that all this powering off has disturbed the loading profile. You can try using Advanced Options for Ubuntu from the boot menu to select Recovery Mode and then Resume. See if that gets you to a working desktop.

Also, you might wish to use Recovery Mode>fsck to check all file systems - partitions

Regards.

Thanks for your reply. I have been trying to solve this issue since I have posted the problem in this forum. What i have seen is that there is some issue with the battery. So if i power on the laptop without the charger then the ubuntu works normally and BTW I am typing this in my ubuntu machine. :)

But if I connect the charger to the laptop then it freezes. 

If i start the laptop with charger then it doesn't reach the login screen. So, I hope it provides more info. For graphics card I have one Intel card which is integrated and the other one is Nvidia 850M. If you need more info do let me know. 

Thanks

PS: If i insert my headphones or any usb cable then it also freezes the whole system and now I am in Win 10 again. :(

---

### Post by Bucky Ball on 2015-11-18
Which model HP are you using and have you checked to see if others are having issues with that particular model? It can sometimes be that specific and need an appropriately specific tweak.

---

### Post by Kinshuk_Lahiri on 2015-11-18
> **Bucky Ball said:**
> Which model HP are you using and have you checked to see if others are having issues with that particular model? It can sometimes be that specific and need an appropriately specific tweak.

HP Envy 15 k-005tx is my model. I can't see anyone with the same model. 3 days ago I installed the 15.04 version and it worked fine and at that time just the restart and shutdown button didn't work.

And then I decided to upgrade to 15.10 and used the software center to update. And the restart and shutdown are working. But when I start it with the power charger or any other USB device is connected or even if the headphone is inserted then, in that, case it freezes the OS. Do let me know if you need any more info.

Thanks.

---

### Post by Bucky Ball on 2015-11-18
Wow. So this is specific to 15.10? :-k If this is the case I'd be very curious to see if anyone else is experiencing anything like that. It'd be a first for me.

A dig around Launchpad may be in order ...

---

### Post by Kinshuk_Lahiri on 2015-11-18
> **Bucky Ball said:**
> Wow. So this is specific to 15.10? :-k If this is the case I'd be very curious to see if anyone else is experiencing anything like that. It'd be a first for me.

A dig around Launchpad may be in order ...


Do let me know if I can help in any way. BTW **grahammechanica, **has told:

[COLOR=#000000][I]It is possible, that all this powering off has disturbed the loading profile. You can try using Advanced Options for Ubuntu from the boot menu to select Recovery Mode and then Resume. See if that gets you to a working desktop.

But I haven't done it yet because I have Windows 10 too. So can you please tell me if I use the recovery mode like graham have said, will it affect my Windows 10 partition in any way?

Thanks [/I][/COLOR]

---

### Post by Bucky Ball on 2015-11-18
No. It won't. Select Recovery kernel, you'll see a lot of text flashing by then eventually get to a screen of options. Choose to continue with boot as per normal (I think that is the top option).

---

### Post by Kinshuk_Lahiri on 2015-11-18
Ok. Let me see. I will come back with my findings :)

---

### Post by Kinshuk_Lahiri on 2015-11-18
> **Bucky Ball said:**
> No. It won't. Select Recovery kernel, you'll see a lot of text flashing by then eventually get to a screen of options. Choose to continue with boot as per normal (I think that is the top option).



Ok I went to the advanced option and there are two recovery options. one with 4.2.x version and another one with 3.19.x so which one to choose?

---

### Post by Bucky Ball on 2015-11-18
Whichever you want to use. Which do you normally use when you're booting a kernel? The 4.2? Do that. Latest kernel.

---

### Post by Kinshuk_Lahiri on 2015-11-19
> **Bucky Ball said:**
> Whichever you want to use. Which do you normally use when you're booting a kernel? The 4.2? Do that. Latest kernel.

Ok I did the recovery mode for the version 4.2 and everything was working fine after that. And then after using the system for 5 minutes, I decided to restart the system but with normal boot now. 

So, I started the system again and selected Ubuntu and hit enter and it again stuck at the Ubuntu logo and this time the orange/white dots were not there. I have tried to start with that mode for 4-5 times and same issue. Do let me know if you need any more info in order to get more idea regarding this problem.

Thanks

---

### Post by Bucky Ball on 2015-11-19
Can you do an update from recovery, please? Might not fix anything but will make sure you're up to date and rule that out.

Boot to recovery and drop to a root shell, then:

```
apt-get update
apt-get upgrade
apt-get dist-upgrade
```

Then continue as you did before to a desktop then reboot normally. Any difference?

PS: You may need to plug a cable in for this update in the recovery mode.

---

### Post by Kinshuk_Lahiri on 2015-11-19
> **Bucky Ball said:**
> Can you do an update from recovery, please? Might not fix anything but will make sure you're up to date and rule that out.

Boot to recovery and drop to a root shell, then:

```
apt-get update
apt-get upgrade
apt-get dist-upgrade
```

Then continue as you did before to a desktop then reboot normally. Any difference?


Yeah sure. BTW

```
apt-get update
```

I have already done that. I will try the remaining 2's to see any difference. Thanks for your help. I will return with my findings.

---

### Post by Bucky Ball on 2015-11-19
'apt-get update' won't upgrade you to the latest kernel for your release, among other things. :)

(You can run 'man apt-get' in a terminal and check the differences between the three update/upgrade commands.)

---

### Post by Kinshuk_Lahiri on 2015-11-19
> **Bucky Ball said:**
> 'apt-get update' won't upgrade you to the latest kernel for your release, among other things. :)

(You can run 'man apt-get' in a terminal and check the differences between the three update/upgrade commands.)

Ok. So I booted to recovery option and there was the option Drop to root Shell. I selected that and entered the first command agt-get update. It displayed a message 

Working 0% and nothing went ahead. The underscore was blinking. I waited for 2-3 minutes and no update so I restarted the laptop and booted to Windows to make the reply. To get the update, I guess Internet connection is important. I do have a working connection. Can you tell me that in the recovery mode when I select the Drop to root shell option, does my laptop gets connected to Wifi or do I have to boot to recovery mode and then select resume normally and then open the terminal and write the commands. :confused:

And also you mentioned above in the PS: To plug a cable in. Can you tell me which cable are you talking about?

Thanks

---

### Post by Bucky Ball on 2015-11-19
Ethernet. You are going to need a cable for the updates.

Yes, you could continue from the recovery mode to the desktop, open a terminal and issue the commands there, then reboot.

---

### Post by Kinshuk_Lahiri on 2015-11-19
> **Bucky Ball said:**
> Ethernet. You are going to need a cable for the updates.

Yes, you could continue from the recovery mode to the desktop, open a terminal and issue the commands there, then reboot.

Ok. So I am now in Ubuntu. I don't have Ethernet cable but do have working WIFi connection. So I opened terminal and entered the command apt-get update and it provided me with the error:

E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

What to do?

---

### Post by Bucky Ball on 2015-11-19
Ah, you now need to add 'sudo' to each of those commands as you are a regular user, not in a root shell. Do:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

You will need to enter your password after the first command. The password will be invisible. This is normal.

---

### Post by Kinshuk_Lahiri on 2015-11-19
> **Bucky Ball said:**
> Ah, you now need to add 'sudo' to each of those commands as you are a regular user, not in a root shell. Do:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

You will need to enter your password after the first command. The password will be invisible. This is normal.


Ok, I have performed these 3 commands. And I restarted and booted to Ubuntu and this time there was complete black screen and it didn't reach the Ubuntu logo. I shut it down and again restarted and then some line of commands started and it froze after some point. I again shut down the laptop forcefully. And when I tried to power on it gave me the same problem. Complete black screen. And taken out the battery to resolve the issue. Do let me know any info you required to help me out of this situation.

Thanks

PS: I did more research. When I start most of the time it gives an error regarding the Bluetooth and error message says that the process has timed out. Hope this will add more clarity.

---

### Post by Kinshuk_Lahiri on 2015-11-19
Any idea?

---

### Post by Kinshuk_Lahiri on 2015-11-19
I have been trying to fix the problem ever since. Now if I use the nomodeset instead of quiet splash in the kernel parameter then I am able to reach the logic screen and it doesn't detect the graphics card. My laptop has dual graphic card. One is Intel based and another one is Nvidia GT-850M and on web someplaces says to install the nvidia drivers and some places says not to install.

Can anyone please tell me what to do?

Thanks

---

