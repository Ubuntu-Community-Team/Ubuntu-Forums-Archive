---
title: "How to check Ubuntu installed properly?"
date: 2023-10-26
forum: Installation &amp; Upgrades
---

### Post by laxmidhar on 2023-10-26
Hi,

I just wanted to check the OS is installed properly or not when i switching on my system i am getting some BIOS error for that i checked with HP support. They told that your OS is not installed properly check with local IT. I remember while OS installation it did not ask for encryption password.
I have attached the screenshot you can refer.
Image_1 : Getting error
image_2 ; Conversation with HP support
image_3 ; I am not supposed to get this screen
Please help me.


Thanks and regards,
Laxmidhar[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292941&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292942&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292943&stc=1[/IMG]

---

### Post by Rubi1200 on 2023-10-26
Hi and welcome to the forums :-)

The ACPI errors are just warnings and can be ignored. Lots of users get those but the system still boots normally.

What was originally installed on the PC and who installed Debian?

---

### Post by laxmidhar on 2023-10-26
Thank you.
Thanks for the response.
What about the 3rd image because i saw in my friends system he was not getting that screen directly it will load the OS but here it is asking Ubuntu, Advance option for Ubuntu and all those.
Can you please guide me?

---

### Post by MAFoElffen on 2023-10-26
What kind of support contract do you have with them? (From the original purchase?) Just standard warranty? Premium support? There is no such thing as "Local IT" for non-commercial.

I was a Certified Onsite Warranty Technician for HP, Dell & Lenovo for a time. I went on both private and commercial onsite calls. HP calls were the least desirable, just because of all the paperwork they wanted done, and the availability of parts. That looked like an automated response. 

It was our policy to call into their Tech Support, and if Onsite with an Ubuntu Issue, I usually had to educate the tier 1 support personnel that "HP does sell some products with Ubuntu pre-installed"... Som of those were custom ordered as pre-installed... then I asked to talk with their supervisor to get to another support tier. Their doc's in tier 1 are for hardware and Windows support.  Of course their online support doc's do refer Ubuntu support to this Forum, and downloading the install media from Ubuntu links... It's not like that is "unknown" to them.

Do you mean that you do not want to see a boot menu of Grub2? Your friend's probably did not show, or was only for moments because it only had 1 OS installed. It says there, that you also have Debian Stretch 9 on there... If more than one OS, then it assumes (rightly) that you might want to have time at the Grub2 boot menu to choose one of the multiple OS'es to boot from. So seeing that "on you machine" rather than your friends) in normal.

---

### Post by Rubi1200 on 2023-10-26
Normally, if Ubuntu is the only system installed it will go directly to the login screen after the boot process is done.

The screen in the 3rd image is the GRUB bootloader. It is showing you the normal options when more than one system is detected. Advanced options are also normal to see.

But, again, the question is who installed Debian on the PC?

I would just leave it as is unless you want to start fiddling around changing grub files on your Ubuntu install.

---

### Post by MAFoElffen on 2023-10-26
(Sniped while editing) Or...

You may choose to edit the grub2 default file to set the timer for that menu to 1-2 seconds so it is not there for long... That way you have a compromise of both.

Or the right thing to do... You may have installed Ubuntu, because Debian 9 Stretch went End Of Support on June 30, 2022. That was over a year ago... It isn't getting any updates any more. That could probably be uninstalled.

---

### Post by laxmidhar on 2023-10-26
Thanks for the response.
I only installed the Ubuntu in the PC.
what is the next step for me.

---

### Post by laxmidhar on 2023-10-26
Thanks for the response.
Can you please guide what to do and how to do?

Thanking you in advance.

---

### Post by laxmidhar on 2023-10-26
As i am new to Linux, Grub2 and Debain so requesting you to please guide the right path.

Thanking you in advance.

---

### Post by ajgreeny on 2023-10-26
The right path is probably to do nothing.

I used to see a similar warning when turning on a laptop with Xubuntu 22.04 recently installed but it booted successfully and over time and normal updating of the OS  those warnings have disappeared.

---

### Post by laxmidhar on 2023-10-26
As i did the minimal installation can someone please guide me how can i open the camera to check the webcam.

Thanking you in advance.

---

### Post by yancek on 2023-10-26
I'm not sure what exactly the problem is that you are posting about.  Does Ubuntu boot as you want it?  The Grub menu you posted shows and install of both Ubuntu and Debian, Debian being on the second partition of the device.  Was that installed when you purchased the computer or did you previously install it?  Does it boot?  Do you want it to boot?  I'm not sure what the problem is and if you can boot Ubuntu as you want, you need to specify what exactly the problem is.  As mentioned previously, if you have only one Linux OS installed and are booting with Grub, it will not show a menu but simply boot the system installed.

With regard to the camera, you should start another thread with a proper title so that members familiar with the software can respond.  The simplest way to see if your camera is functioning is to open a terminal and simply type:  cheese  Cheese is software that uses the camera and should/might be installed by default.  If it is functioning, when you type cheese in the terminal you should see a screen showing whatever is in front of the camera, generally that would be the person sitting at the computer.  If you have problems with this, make note of what you did and the results and start a new thread for the problem.  Depending upon what you want to use the camera for, you will likely need to configure specific software for your particular use case.

---

### Post by MAFoElffen on 2023-10-26
When you do open that new thread, please run the 'system-info' script, but add the "--details" starup option to the end of the command. Post the URL of where that uploads to in your post.

That will tell members here information on your hardware and what is installed so we don't have to ask you 50 questions and commands to run to get that information. Much easier on all of us.

That will also give us a little information on the Debian Install there and what to do with it. You may need more room, to install other things...

Why? because you just mentioned that you installed Ubuntu Desktop as "minimal". Which a minimal install, to save space, does not include many things such as software for video and media... You see where that seems to be important to you now, but was affected in how you installed Ubuntu? That you possibly may need more room?

---

