---
title: "Problem when trying to install ubuntu mini.iso"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by Fxy on 2012-07-06
Hi

I'm looking to install the ubuntu mini.iso, but the computer that i'm trying to install it on uses a **Micro NEXT MN-WD550M** wireless dongle.  Is there anyway i can install using the wireless dongle :?  If not i have a macbook that i can connect to the computer via ethernet if thats any good :?



Fxy...

---

### Post by Cheesehead on 2012-07-06
You seem to have asked this question before: [http://ubuntuforums.org/showthread.php?t=1981914](http://ubuntuforums.org/showthread.php?t=1981914)

What was the result of that attempt?

In that thread, you said that the wireless dongle worked quite well. Has something changed?

---

### Post by Fxy on 2012-07-06
I never found a fix, but just resorted to using xfce instead.  The dongle works perfect out of the box if i install any new releases like ubuntu/kde/gnome/lxde etc etc.  All i need to know is how to work the whole internet connection thing so that i can get this installation rolling...  I currently have lubuntu installed on the computer & wonder if instead of using the mini.iso, is there anyway i can uninstalling everything bar openbox & what is needed for the computer to run :?



Fxy...

---

### Post by Cheesehead on 2012-07-06
You haven't told us what the problem is. You want to do an install with a wireless dongle, Have you tried? What happened?

Is it an install failure? Unable to connect to the network? Dongle not recognized by the system? Is there an error message? 

What are the symptoms?
How can we reproduce the problem?

---

### Post by Fxy on 2012-07-07
Ok so i cant get past the internet connecting part !!  It goes through the detection of my internet etc etc, but stops with DHCP saying **network autoconfiguration failed. Your network is probably not using the DHCP protocol.  Alternatively, the DHCP server may be slow or on some network hardware is not working properly.**  Once i click on continue the only options that i have are **retry network autoconfiguration**  /  **retry network utoconfiguration with a DHCP hostname[/B  /  [B]configure network manually** & **do not configure the network at this time**  

Its almost as if the dongle goes undetected or something !! How do i get past this point :? Or how do i configure it manually :? Could i get this working via maybe connecting a ethernet cable from my macbook to the computer :?



Fxy...

---

### Post by Cheesehead on 2012-07-07
> **Fxy said:**
> Its almost as if the dongle goes undetected or something !!

Quite the opposite. What you are describing indicates that the wi-fi dongle has been detected, configured, and is in use by the operating system.

There are three main possibilities. Try to eliminate one. Either your wireless network (configuration, signal strength), or the dongle has a problem, or the incorrect kernel module is being loaded.

Tell us about your wireless: Do other machines properly connect using dhcp? Is the signal strong enough to reach your location? How do you know the signal isn't too weak?

Try using the command line. Use the command [FONT="Courier New"]lsusb -vv > /tmp/lsusb[/FONT] to create a file called /tmp/lsusb. Post the contents of the file here. That will tell us if the dongle is currently assigned the correct kernel module (driver).

Use the command [FONT="Courier New"]dmesg | grep wlan > /tmp/dmesg-wlan[/FONT] to create a file called /tmp/dmesg-wlan. Post the contents of the file here. That will tell us how the dongle was assigned at boot, and any kernel error messages.

---

### Post by Fxy on 2012-07-08
> **Cheesehead said:**
> Quite the opposite. What you are describing indicates that the wi-fi dongle has been detected, configured, and is in use by the operating system.

There are three main possibilities. Try to eliminate one. Either your wireless network (configuration, signal strength), or the dongle has a problem, or the incorrect kernel module is being loaded.

Tell us about your wireless: Do other machines properly connect using dhcp? Is the signal strong enough to reach your location? How do you know the signal isn't too weak?

Try using the command line. Use the command [FONT="Courier New"]lsusb -vv > /tmp/lsusb[/FONT] to create a file called /tmp/lsusb. Post the contents of the file here. That will tell us if the dongle is currently assigned the correct kernel module (driver).

Use the command [FONT="Courier New"]dmesg | grep wlan > /tmp/dmesg-wlan[/FONT] to create a file called /tmp/dmesg-wlan. Post the contents of the file here. That will tell us how the dongle was assigned at boot, and any kernel error messages.

Ok so the dongle is detected, that's a good thing now.  I know the signal from the router to the dongle / computer is good because I have the latest version of lubuntu currently installed & the internet on it works fine straight out of the box.  Ive never came across dchp before until i started trying to use this mini.iso so I wouldn't know !!  I have a MacBook & sont vaio laptop that both just pick up the wireless internet & away they go. It's basically the same with the computer bar when I'm using this mini.iso haha. Ok so those 2 commands, I'll just run them from my current installation :? Or from the mini.iso :?



Fxy...

---

### Post by Cheesehead on 2012-07-08
> **Fxy said:**
> Ok so the dongle is detected, that's a good thing now.  I know the signal from the router to the dongle / computer is good because I have the latest version of lubuntu currently installed & the internet on it works fine straight out of the box.

Wait a second...the dongle works just fine in the current location with a current Linux install?
That's important information.

Where did you get the mini .iso from? Is it up to date? Can you get to a command line on it? (If so, run those two commands on it so we can compare)

---

### Post by Fxy on 2012-07-08
I got the iso from the ubuntu website a few months back !!  I also today downloaded the ubuntu alternative intel today, but when it boots i cannot select anything on the menu.  All the  menu option just give me a beep sound :?



Fxy...

---

### Post by Fxy on 2012-07-09
FYI : Command line on the mini.iso :?  Do I have to press a button or anything, because there is no option given for command line :?  There is a command line install option when I first boot by it just seems to appear like the normal option that I've been trying !!

Ohhh is there a way I can completely remove my lubuntu desktop & only have the necessarys to boot straight to openbox :?


Fxy...

---

### Post by Cheesehead on 2012-07-09
All these short answers are very confusing. 

Is your problem still the wireless dongle? Do you actually know that the wireless dongle doesn't work? If so, how do you know? Be specific. Is there an error message?

Is your problem that your are you having some kind of trouble installing? You have talked about some successful install, some problems with the minimal and alternative images, but without enough detail to help. If there's an installer, then please tell us exactly which image you are using, which options you are selecting, and where exactly in the process it fails, and give an exact copy of any error message.

---

### Post by Fxy on 2012-07-09
> **Cheesehead said:**
> All these short answers are very confusing. 

Is your problem still the wireless dongle? Do you actually know that the wireless dongle doesn't work? If so, how do you know? Be specific. Is there an error message?

Is your problem that your are you having some kind of trouble installing? You have talked about some successful install, some problems with the minimal and alternative images, but without enough detail to help. If there's an installer, then please tell us exactly which image you are using, which options you are selecting, and where exactly in the process it fails, and give an exact copy of any error message.

Ok so my problem is still with the dongle & mini.iso minimal install.  Whenever i start the installation it gets to the point where brings up dhcp like described before.  I actually cannot get past this part to continue with the installation !!  Also the problem with the alternative cd is that when i boot it up i just get to the first screen ( e.g boot to ubuntu, install ubuntu etc etc ) but whenever i select anything i just get a beep in return :?  Even when i leave it on the first option it just automatically trys to select it but i still only get a beep on return :?  I know that the dongle works because i currently use it on the computer that im trying to install the mini.iso on !!  I have tried the dongle with the latest versions of ubuntu, kubuntu, lubuntu, xubuntu & a few others & it seems to work perfectly on them all.  I should mention that the only time the dongle does not work is when i try to use an older linux os like ubuntu 8.04...

...What i am really trying to accomplish is to have only openbox installed, along with the few apps that i currently use.  Since i seem to be having trouble with the mini.iso, im wondering if there is any way that i can wipe/erase everything on the computer bar what is required to run openbox :?



Thanks for all the help so far.

Fxy...

---

### Post by dino99 on 2012-07-09
as your system have an other ubuntu (lubuntu) installed, then tweak grub to run netinstall to do the new installation

[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by Fxy on 2012-07-09
> **dino99 said:**
> as your system have an other ubuntu (lubuntu) installed, then tweak grub to run netinstall to do the new installation

[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

Thanks for the link but that does not help me in any way with getting past my internet problem !!



Fxy...

---

### Post by Fxy on 2012-07-10
> **dino99 said:**
> as your system have an other ubuntu (lubuntu) installed, then tweak grub to run netinstall to do the new installation

[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

Thanks that seemed to wörk :-)} 



Fxy...

---

