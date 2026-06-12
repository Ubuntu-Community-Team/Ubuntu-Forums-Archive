---
title: "Can't Install"
date: 2015-06-22
forum: Installation &amp; Upgrades
---

### Post by thomas35 on 2015-06-22
First I download Ubuntu  (which takes 2 hrs. on this provider's system.)  Then I move it to a USB. Then I go to check the USB to make sure everything is kosher, I get the message. "File is too large for notepad.  Use another editor to edit the file."  I don't wanna' edit the file.  Then I tried to boot from the USB  with fingers crossed.  I ended up having to go into the BIOS and changing the boot order.  Then I got a message telling me to 'remove all media.' And then it booted into Windows.  Anybody  know what's  going on? (I  may sound more knowledgeable than I really am. I have just fooled around a lot and gotten lucky.) Oh - I  have Vista - which is a large part of why I am anxious to try anything else.

---

### Post by TheFu on 2015-06-22
Ubuntu needs partitions on the HDD to install into - at least 2, perhaps 5 are needed - plus the space to hold it.

So ... if you don't see the screens in this link [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop) , then you haven't installed it.

If you want guidance about partitioning, plus run the **boot-info** script under a live-boot Ubuntu environment - there are links and instructions in my signature.  Most of the time, I'd suggest you run **boot-repair**, but since your bandwidth is painful to use, maybe that isn't the best option for you?

---

### Post by yancek on 2015-06-22
How did you get the Ubuntu iso file you downloaded onto the USB?  Generally, one needs specific software to put it there so it will be bootable.  Unetbootin, pendrivelinux are just two examples which can run on windows.  I don't know how notepad would fit into this scenario?  If you set the usb drive to first boot priority and got that message, it is quite likely the usb is not bootable.  Check the download with md5sum and also post back how you put Ubuntu on the usb drive.

---

### Post by TheFu on 2015-06-22
> **yancek said:**
> How did you get the Ubuntu iso file you downloaded onto the USB?  Generally, one needs specific software to put it there so it will be bootable.  Unetbootin, pendrivelinux are just two examples which can run on windows.  I don't know how notepad would fit into this scenario?  If you set the usb drive to first boot priority and got that message, it is quite likely the usb is not bootable.  Check the download with md5sum and also post back how you put Ubuntu on the usb drive.

It is possible to use **dd** or **ddrescue** to shove an ISO onto a flash drive. I know - but it works. However, dd can trash a system if the wrong data is entered in the wrong places. Be aware and be careful.

If you want to make a multi-OS boot flash drive with 2-20 different installers/liveBoot ISOs, I've had the best luck with yumi - find it at pendrivelinux too. [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

---

### Post by mastablasta on 2015-06-23
this is how you put Ubutnu on USb (but there are other options such as previously mentioned): [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

iso image can be opened in program total command and probably some others as well. but you don't want to do that. that's not how you check if all is good after download. this is how you do it: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Ty_Scheun on 2015-06-23
As what mastablasta said, you cannot move the ISO into the drive by itself. It will cause it to not be bootable probably because your computer doesn't know what to do with an ISO file. Use UNetBootin or Pen drivelinux to make your USB Drive bootable.

---

### Post by thomas35 on 2015-06-24
I figured out part of my problem.  But first, this comment/question.  I kept  expecting a notification by email of replies here, so I figured that since there weren't any notifications, there  weren't any  replies.  It was only by accident that I found myself back here.   And then, in order to reply, I had to sign up for an Ubuntu One account.  Although it was fairly easy to do - only desperation made me do it.  The last thing I needed today was more geek speak.  So, anyway, how do I get notifications?

In my great wisdom (!?:lolflag:). I decided to make my USB all clean and shiny.  So I formatted it.  Windows lets you do that, so it must be ok to do it, right?  Um, yeah right.  If I'm not mistaken, I just made my USB more or less useless.  I did go through the pendrivelinux route to get the file on the drive, but as somebody mentioned, the file by itself is unbootable.

I have a  PC in addition to the laptop I am trying to put Ubuntu on, so doing another download is certainly doable.  Right now the plan is to buy another USB and  start over.  Is there some safe way I can restore the USB to usability?

---

### Post by sudodus on 2015-06-24
USB pendrives are good as temporary devices. Use it for one thing, wipe it and re-use for another thing. ***Gparted*** is a good tool for not only formatting the file system, but also change the partitions, if you wish. Gparted comes with the Ubuntu install iso file (the live system). If you want to use it in the installed system, you must install it, which is easy from the Software Center.

You can re-use the pendrive before wiping it. It should work to boot and install Ubuntu also into the other computer, unless it is so different, that you need another version or flavour of Ubuntu or even another linux distro. And after that you can wipe and reuse the pendrive for transfer of files or whatever.

---

### Post by TheFu on 2015-06-24
Your USB drive is probably fine. Just reformat it. 

Explanation: There are many different file systems - windows uses fat, fat32, exfat, ntfs.  Linux has about 20 different file system types - Windows doesn't know anything about these - which I'm guessing is the issue you are experiencing. If windows refuses to do anything, use gparted like sudodus suggests.

Sorry that our "geek speak" scares you. Technical terms must be used. Look them up if you don't understand - or ask.

---

### Post by thomas35 on 2015-06-26
The geek speak doesn't scare me.  You just assume I know things because to you, they're obvious.  Like the term "Software center".  What does that mean?  Just the term "pendrive" -  I finally figured out that's just another name for what I am used to calling a thumb drive or USB drive.  But it threw me.

So if Gparted is part of the ISO file, and Windows doesn't recognize the file type - how do I get into it?  I would guess I need to install Gparted first in order to open the ISO file?

And nobody addressed my question about how to get notified of posts on here.  If that's not possible, what's an easy way to find these posts?  This is all  new to me so I appreciate your patience.  I am 60 and did not grow up with computers.

---

### Post by sudodus on 2015-06-26
> **thomas35 said:**
> The geek speak doesn't scare me.  You just assume I know things because to you, they're obvious.  Like the term "Software center".  What does that mean?  Just the term "pendrive" -  I finally figured out that's just another name for what I am used to calling a thumb drive or USB drive.  But it threw me.

The Ubuntu Software Center is a program, that comes with Ubuntu, and that you can start from the dock on the left edge of the screen or from dash (the tool to search for programs in Ubuntu).
> 
So if Gparted is part of the ISO file, and Windows doesn't recognize the file type - how do I get into it?  I would guess I need to install Gparted first in order to open the ISO file?

Gparted is also started from dash (the tool to search for programs in Ubuntu).
> 
And nobody addressed my question about how to get notified of posts on here.  If that's not possible, what's an easy way to find these posts?  This is all  new to me so I appreciate your patience.  I am 60 and did not grow up with computers.

I don't want my mailbox spammed with notifications. But you can subscribe for more or less notifications.

Click on 'Settings' at the top right corner

In the left column you find 'My settings' with 'My account'

Then in the main column of the page you select 'Default Thread Subscription mode'

---

### Post by TheFu on 2015-06-26
> **thomas35 said:**
> The geek speak doesn't scare me.  You just assume I know things because to you, they're obvious.  Like the term "Software center".  What does that mean?  Just the term "pendrive" -  I finally figured out that's just another name for what I am used to calling a thumb drive or USB drive.  But it threw me.

So if Gparted is part of the ISO file, and Windows doesn't recognize the file type - how do I get into it?  I would guess I need to install Gparted first in order to open the ISO file?

And nobody addressed my question about how to get notified of posts on here.  If that's not possible, what's an easy way to find these posts?  This is all  new to me so I appreciate your patience.  I am 60 and did not grow up with computers.

I'm not much younger than you are. My family didn't get a computer until I was about to graduate from college. For most technology things, I'm a late adopter.

So, I didn't use either of those terms, but google is a great tool for picking up ideas about what things are: "Software center ubuntu" or "pendrive ubuntu" would take you to helpful descriptions, should you enter those terms into a google search area. Should work for most search engines - however, bing search just doesn't find Linux things as well.

[http://ubuntuguide.org/wiki/Ubuntu_Trusty](http://ubuntuguide.org/wiki/Ubuntu_Trusty) is an easy-to-understand instruction set for Ubuntu Desktop.  No need to read it - just skim it quickly to see what is possible. There is another source for the newest release [https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/) (which I don't run). I prefer to have the longer LTS support, so only run LTS releases which get 5 yrs of support. The other releases only get 6-9 months of support - this is just too short for me to switch. "Support" - that means security patches. If an OS doesn't get security patches, I don't want it.

The last suggestion I have is to visit your local LUG. [https://en.wikipedia.org/wiki/Linux_user_group](https://en.wikipedia.org/wiki/Linux_user_group) - there you should find real people, local to your city, willing to help with questions.  My LUG meets every Sunday afternoon just to help people new to Linux get over that first hump. 15 minutes of questions can save many days of misunderstandings.  Plus we provide links to learn more based on the background of the person trying to get started. Having a real person across the table really does matter for communication when the vocabulary isn't there yet.

BTW, we were all new to Linux at some point. I remember struggling to understand things too. We've all been there.

---

### Post by thomas35 on 2015-06-30
Are you really in Atlanta?  I am 3 hours due north of you in Sylva, NC.  Thanks for the info on LUG's.  But since I am disabled and don't drive, if it ain't solvable via the online route, it ain't happenin'.  Eventually I will get it figured out.  I really hate M'soft, so I'm motivated.  

I followed one of the links you provided, knowing I could just hit the "back" button and return to this post.  Uh, no.  I got "back" to a page of all the open threads, had to search for this one again and of course - lost everything I had written earlier.

---

### Post by thomas35 on 2015-06-30
When I try to change my notification settings, I get this. "
**thomas35**, you do not have permission to access this page. This could be due to one of the following reasons:
  
[LIST=1]
[*]If you have made fewer than 10 posts, access to your personal settings is restricted. See [here]("http://ubuntuforums.org/showthread.php?t=2034393") for more details."  {sigh, sigh and more sigh}.
[/LIST]

This is NOT an easy site to navigate.

If you need to get into the Software center to create a bootable USB drive (as per the instructions), but the Software center is part of the OS I don't have yet. . .   It's pretty amazing that I haven't pulled out my remaining hair.  Time for a beer and less Ubuntu for a while.  I sure hope this is better than Vista (though I imagine about anything would be.)

---

### Post by oldfred on 2015-06-30
I always use Advanced Search on forum. 
If I just put my user name in and search it shows all threads I have posted in, with those with new posts at top & in bold.

---

### Post by TheFu on 2015-06-30
> **thomas35 said:**
> Are you really in Atlanta?  I am 3 hours due north of you in Sylva, NC.  Thanks for the info on LUG's. 
[http://wnclug.ourproject.org/](http://wnclug.ourproject.org/)  I guessed on which group was closest. There might be even closer groups. Check any local colleges.

---

