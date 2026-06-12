---
title: "Ubuntu 16.04 upgrade from 14.04 wrong conf file for multiple monitors"
date: 2016-05-10
forum: Installation &amp; Upgrades
---

### Post by crazybear on 2016-05-10
A few problems with the upgrade, but generally it went smoothly. I have a three monitor system run on a newish AMD card. Works fine in 14.04.3. I know all about how 16.04 doesn't allow flgrx anymore. I assumed it would install system AMD drivers correctly. I first got only one monitor, now two without doing anything - but they are each just copies of one another and the third is black. I need to once again have one large desktop. Computer lists that I only have one monitor and even that can not be adjusted properly. I hunted for the conf file that might be the problem and found my old conf file still there listing 'aticonf-monitor'-0/1/2 (and aticonfig-device, etc.), and assume this is my main problem - my old configuration file being used(?). However, I do NOT know what the new conf file should say nor the exact name of the conf file 16.04 will look for first [there are several in 14.04, and also now still in 16.04]. If anyone can help out, would be MUCH appreciated! All screens also do not show the desktop image I have selected when in Gnome fallback, though it does show it (weirdly) in just plain 'Gnome', but assume part of the problem could be the configuration file for the monitors. Thanks in advance. N.B. anyone have any idea when some better support of AMD will happen for Ubuntu 16.04?

---

### Post by grahammechanical on 2016-05-10
The release notes say this:

> When upgrading to Ubuntu 16.04 from a previous release, both the fglrx  driver and the xorg.conf will be removed, so that the system is set to  use either the amdgpu driver or the radeon driver (depending on the  available hardware). 

You should be using amdgpu. Can you confirm this with the Details page or Additional Drivers. You may be running on a fallback open source video driver call Mesa llvmpipe. 

As for when there will be any progress in AMD open source video drivers opinion is pointing to the summer.

[https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)

Regards

---

### Post by crazybear on 2016-05-10
> **grahammechanical said:**
> The release notes say this:



You should be using amdgpu. Can you confirm this with the Details page or Additional Drivers. You may be running on a fallback open source video driver call Mesa llvmpipe. 

As for when there will be any progress in AMD open source video drivers opinion is pointing to the summer.

[https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)

Regards

Thanks for the reply. Well, the flgrx drivers ARE gone, but the xorg.conf files and the X11 folder is still there [assume it is ignored by the system]. Additional drivers shows me no options available and none in use. I see nothing yet on how to set up multihead configuration [nor where! - what config file] in 16.04 for AMD. There are lots of help threads for this in other earlier versions. I can't use 16.04 as it is. When it starts up after login, I briefly see the correct desktop image, but with some very odd black artifacts of geometric shapes over it...then it goes to black and stays black. However, when I open a program or watch live streaming or a video, etc. all is very clear...so some driver is working, in part, at least. I opened up Package Manager and looked at what might be installed or available. nothing 'mesa' that seemed to be connected to video was installed. No fglrx drivers were installed. some 'radeon' drivers were installed but their properties seemed to indicate they only helped with GL acceleration, amdgpu drivers seemed to be installed....but obviously the system thinks I have only one monitor - HOW DO I TELL IT I HAVE THREE? and IN WHAT FILE do I tell it this?! August is a LONG time off and those kinds of things tend to drift even further...... It seems it should work with the Linux drivers...I'm not a game player, I just need a very large destop for what I do. Help and/or suggestions of what next to do or try very much appreciated.

---

### Post by crazybear on 2016-05-11
OK, I think [MAYBE?!] I found the config file in 16.04. Below is what is says and what two working xorg.conf files in the past read. I'd really really appreciate it if someone could help using past information instruct me how to get 16.04 to see and correctly use my three monitor system! [ATTACH]268987[/ATTACH]

---

### Post by crazybear on 2016-05-13
Maybe I wrote too early. I know amdgpu is INSTALLLED. I do NOT know it is being used as the driver. How would I find out. Nothing shows under additional drivers except a audio driver for my gpu [not selected]. Can anyone tell me if the structure of the monitor config file follows the same or same basic format as in prior versions [14.04 or 12.04], and where the hell the file is located and what it is named?! Somewhere I saw a post that someone had successfully got 3 monitors running with 16.04 - but now can't even find this post and don't remember if he had nvidia or AMD. Needless to say, I'm not using 16.04, as I have other versions that work...and hope someday I can get help to make 16.04 work with my three monitors, as well.

---

### Post by crazybear on 2016-05-13
I solved most of the problem! I now have three monitors recognized! I did a search for the command to see what driver is active for the video [ lshw -c video ] and it gave a strange error message. I then uninstalled every file named flgrx* and to my surprise they had NOT been removed in the upgrade [as I had assumed - and synaptic seemed to indicate]. After they were removed and I rebooted, almost everything was fine. Now, only the desktop image doesn't show and the item on the desktop don't show, but can be found if under Places I look in Desktop...so getting there slowly. What a battle.

---

### Post by crazybear on 2016-05-14
I spoke [wrote] too early that all was fixed. Thought it was, but now the monitors are not in the correct order and I see no way to order them other than to know where the config file is and how to change it...though I think I can figure that out if someone would tell me where it is and what it is called. The is a program to handle the monitors, but I tried all variants and things only got worse. It doesn't allow one to move the monitor it considers 'primary'...and that is likely in the wrong location.
Moving the mouse or panel only to have it jump into a non-contiguous area is very upsetting. Thanks.

---

