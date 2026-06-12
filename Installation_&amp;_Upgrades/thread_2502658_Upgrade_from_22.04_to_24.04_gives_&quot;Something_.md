---
title: "Upgrade from 22.04 to 24.04 gives &quot;Something Seriously Wrong Has Happened&quot; error"
date: 2024-11-23
forum: Installation &amp; Upgrades
---

### Post by hennmann on 2024-11-23
I have 22.04 with the Jellyfish desktop on a 2016 vintage MSI Krait Edition AM3+ with FX8570 CPU. This is also a dual boot system with Windows 10 Pro on one partition and Ububtu 22.04 on another and Windows is working fine with full internet access so there are not hardware problems at the current time. 
I did a FULL update using sudo apt update and after I entered this I entered sudo apt upgrade all and it indicated 22.04 was totally updated. 
Next I entered  

sudo apt update && sudo apt upgrade

 and I believe I entered this BUT I use copy and paste from instructions I found online using CLI to do an upgrade and my CLI displayed all the same information as what was shown in pictures with the instructions showing what to expect.
NOW there were some suggestions or instructions I ignored such as backing up the system which I didn't do because over the years my upgrades ALWAYS went smoothly because after all this isn't Windows&#129315; and the second was 
Prepare TCP Port 1022. 
I didn't follow this step either.
Anyway when I started and went through all the instructions presented on CLI it reached the point of everything going normally but I recieved a notice that Firefox needed SNAPS and proceeded and it indicated " connecting to server failed" and gave me the option to retry, abort, and skip and also indicated if this was not done my Firefox would become inoperable so after a number of retry attempts I selected abort and that was that. I didn't enter exit on CLI either and perhaps this was a big no no?
The system was otherwise working fine and rebooted and got the white screen showing a picture of a monitor with X's in the eyes on the monitor and the notice "something seriously wrong has happened. Please contact system administrator"
On my boot loader I have the option for other Ubuntu boot options and picked an earlier version in recovery mode and this doesn't seem to work.
Is there a way to bring up CLI and enter instructions for performing a recovery of damaged or missing system files?
Now what is an easy way to attempt recovery and repair? 
Use a USB thumb drive with 22.04 installation media?
Is there a way to bring up CLI at my advanced boot options from my boot loader? If there is, what commands can I enter to get my OS to connect with Ubuntu servers t download and install or is the thumb drive .ethode perhaps a better option?

---

### Post by hennmann on 2024-11-24
Since nobody seems to respond, can my failed upgrade be repaired using a Ubuntu 24.05 installation USB??

---

### Post by Tadaen_Sylvermane on 2024-11-25
Unfortunately "something has gone seriously wrong" is pretty much a useless message. You can boot into a live image to and chroot into the system to fix or chase whatever it is. Its not for the faint of heart though. You would need to check the log files which should be in /var/log. Check the snap and apt logs. Then try to go from there. That being said once you are live booted into a chroot you should have no trouble accessing your personal data. From there you can back it up and do whatever is the easiest method for you. While Linux theoretically shouldn't need to reinstalled pretty much ever sometimes it's the quickest and easiest way to go about it. It just depends on how much damage was done. And again.. that message is pretty useless. 

My personal suggestion is to backup your data first from a live image. Then once you chroot in maybe try an ```
apt install -fy
``` from the chroot and see if it does a bunch of stuff, this will likely (not guaranteed) get you a bootable system as the update just functions with the apt command. It sounds like packages just never successfully configured. Only a guess though.

For the chroot I recommend mounting your temp style directories into the chroot as so. Learned this from Arch wiki. $CHROOT being wherever you have the system mounted at.

```
for i in sys dev run ; do
  sudo mount --make-rslave --rbind /"$i" /"$CHROOT"/"$i"
done
sudo mount --bind -t proc /proc /"$CHROOT"/proc

```

This should eliminate any troubles with needing these directories for package installation and it will think it's actually booted with a fully functional system behind it.

---

### Post by hennmann on 2024-11-25
It is anything but fully functionable and with my bootloader for advanced features using a previous version to restore, that doesn't work. All I got is CLI and when I select sudo apt update it gives me a list of Uninstalled snaps or "broken" snaps.
sudo apt update and sudo apt upgrade do nothing and yes it has internet/network access as well. 
Using a USB flash drive and running in live and attempting to repair it by installation is also nonsense. It does NOT tell me which partition the Ubuntu OS is in or my Windows, it does not inform me I already have OS's present and it sure as heck doesn't ask me if I want to repair what is there or even upgrade!!
If I slap in a Windows DVD it most certainly presents all of these options!
Yes I have pictures taken on my Android phone and cannot find a way to post them as well&#128545;.
Yes there is also a Ubuntu group on Facebook but here I sit with "pending approval by administrator" and the so called administrator doesn't seem to be very fast and is as fast as a snail stampeding through peanut butter!!

---

### Post by hennmann on 2024-11-25
I might add that Ubuntu 22.04 WAS fully functionable and behaving normally after I selected abort. Now all I have is a CLI telling me what is allegedly broken. 
IS there a way this can be rectified using a USB drive and the so called live??
How long have I been using Linux but with limited knowledge of CLI comands? I go back to Mandrake and even earlier and back then you were expected to FULLY setup partitions, what the partitions were for including swap and now everything is fully automatic or with considerably limited options!
I guarantee most new users have zero knowledge of partitions and how to set them up along with other steps we used to have to do during installation.

---

### Post by yancek on 2024-11-25
>  Now all I have is a CLI telling me what is allegedly broken. 

You haven't posted what those error messages are so there isn't any way to tell you how to repair what we don't know isn't working.  If you have a cell phone and take pictures of the screen you can upload them by clicking on the paperclip icon in the top line of icons above your input box when you are posting.  When that window opens, click on Add File in the upper right.

Do you happen to have a link to whatever site you were using to follow instructions or did you make note of what these instructions were?
The link below discusses multiple ways to boot to a command line.  If you make any of these changes so you will know what to change bak later.

[https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode](https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode)

The link below explains upgrading from 22.04 to 24.04.  Does any of that look familiar?  Do you see messages regarding broken packages?  If so, are they snaps or standard? 

[https://www.cyberciti.biz/faq/how-to-upgrade-from-ubuntu-22-04-lts-to-ubuntu-24-04-lts/](https://www.cyberciti.biz/faq/how-to-upgrade-from-ubuntu-22-04-lts-to-ubuntu-24-04-lts/)

If you have broken packages, the link below might help but not for snaps.

[https://phoenixnap.com/kb/ubuntu-fix-broken-packages](https://phoenixnap.com/kb/ubuntu-fix-broken-packages)

---

### Post by Tadaen_Sylvermane on 2024-11-25
> Using a USB flash drive and running in live and attempting to repair it  by installation is also nonsense. It does NOT tell me which partition  the Ubuntu OS is in or my Windows, it does not inform me I already have  OS's present and it sure as heck doesn't ask me if I want to repair what  is there or even upgrade!!

> How long have I been using Linux but with limited knowledge of CLI  comands? I go back to Mandrake and even earlier and back then you were  expected to FULLY setup partitions, what the partitions were for  including swap and now everything is fully automatic or with  considerably limited options!

Sorry these 2 statements don't jive. You know how to setup and configure partitions but you can't figure out which partition is the one you need to screw with? If you actually had the experience you say you do (not trying to start a fight) it should take you less than 2 seconds to find out the right partition. Something about this doesn't add up. You either know what you are doing or you don't. If you can't even determine what partition is what without a gui telling you then your best option is to reinstall. And no version of Linux in my experience has any type of "repair" option. As mentioned since you haven't posted useful information there is little anyone can do but guess. So it's impossible for anyone to offer anything remotely useful. Take a breather, look some things up, then try them. If that is to much then just reinstall and move on with your life. Just because it CAN be fixed doesn't always make that the best option.

---

### Post by grahammechanical on 2024-11-26
I have also seen that "Something went seriously wrong - call an administrator" message. In a business situation that makes sense but the home user is the administrator. And without any indication of what has gone wrong how would anyone know what to do to fix it. I can explain this comment. Not that it will help with the problem.

> but I recieved a notice that Firefox needed SNAPS

Firefox in Ubuntu 20.04 is a deb packaged application but in 24.04 it is a snap packaged application. So, we are warned about the transition. This I think is a clue:

{QUOTE]it indicated " connecting to server failed"[/QUOTE]

Did the connection to the internet break? And then there is this:

> I didn't enter exit on CLI either and perhaps this was a big no no?

With hind sight and looking at someone else's problem, I would say the reboot loaded an improperly shutdown Linux with an incomplete upgrade to the next version.

My memory is not clear but an update/upgrade broke an install of Ubuntu 20.04 bringing the "Oh, No" message. Over several days I tried using recovery mode update/upgrade in the hope that some magic would occur. Then I gave up and switched to using Ubuntu 22.04 I was dual booting with. Months and Months later I gave 20.04 another try before re-using its partition. Hundreds, and I mean hundreds of packages (close to 500) were downloaded and installed. After "exit" > Resume the OS loaded to a working Ubuntu 20.04. Magic.

You can re-install over the broken installation. You can put in a new install on new partitions and dual boot and then recover your data. Perhaps setting aside a partition just to hold data. So, that a broken OS doesn't prevent access to data. This is what I do.

Regards

---

### Post by yancek on 2024-11-26
Another option might be to reinstall and NOT format.  If Ubuntu is all on one partition it is possible to reinstall and not format and and it will put all the proper files in place and basically, repair the system.  I've done this several times with another Linux OS and it went well and I didn't lose any personal data.  Since the OP indicates no backups, I would first do that because there is no guarantee with any method.

---

### Post by hennmann on 2024-11-28
I'm still floundering and am reluctant to reinstall without formating simply because while in "live" it will not tell me where my damn Ubuntu is located&#129324;! I have multiple hard drives and multiple partitions and a plethora of hard drives and partitions listed with NO description of what any are. While using file manager I can look inside and see my windows and Ubuntu BUT unless I know EXACTLY where everything is, this can be a total recipe for disaster! 
Of course I could post pictures but when I select Manage Attachments  I see absolutely no indications of my pictures on my smartphone. Am I supposed to go into this forum using my working Windows OS and email pictures to myself?
I was able to enter CLI on my grub bootloader using Advanced options but selecting recovery only tells me my system is busted and doesn't allow me to enter any commands other than send error report, cancel, etc. and my previous CLI where I could enter commands IS GONE&#128545;!
How do I enter a usable terminal at my grub bootloader? 
Since this is shaping up to be a total disaster I may as well start disconnecting my hard drives so nothing else gets wrecked! 

First things first!
How do I enter CLI and a USABLE CLI at my grub bootloader?
If I can what commands can I enter to attempt to recover and PLEASE Recovery Mode is useless despite any of the versions I select.
Since "Live" is running in RAM how can I attempt to enter my broken system? 
What am I doing wrong that I cannot even post a picture on this forum even while in full site instead of mobile?? 
Yes I have 24.04LTS on a thumb drive but it is little use if I don't know proper procedures.
First I need to get my Terminal back at the bootloader!

---

