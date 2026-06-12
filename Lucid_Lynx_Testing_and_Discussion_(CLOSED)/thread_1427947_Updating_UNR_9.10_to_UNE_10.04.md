---
title: "Updating UNR 9.10 to UNE 10.04"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by victor9098 on 2010-03-12
Just a quick question,

To try and keep my settings I used the upgrade option to go from 9.04 UNR to 9.10 UNR, but when the update was complete I ended up with the desktop edition and not the UNR.

Has anyone used the option to update from 9.10 UNR to any of the 10.04 UNE aplphas?

I am currently downloading a full copy to do a fresh install, though would prefer to just update, but not if I end up with the desktop editon.

Thanks

---

### Post by VK7HSE on 2010-03-13
Hi...

I'm wondering if at some point you may have essentially un-installed the UNR meta package (ubuntu-netbook-remix) and the update has assumed that you were on a desktop install? (ubuntu-desktop)

just a thought...

---

### Post by haddog on 2010-03-18
Any sites with screenshots?

---

### Post by haddog on 2010-03-20
Not many posts here.

---

### Post by victor9098 on 2010-03-20
> **VK7HSE said:**
> Hi...

I'm wondering if at some point you may have essentially un-installed the UNR meta package (ubuntu-netbook-remix) and the update has assumed that you were on a desktop install? (ubuntu-desktop)

just a thought...

It happened to me and to a friend, I guess there is a chance we both did that at some stage but I do not see how. Would it have had any other knock on affects?

In the end I just did a fresh install with the then UNE A3 rather then risk the messing of updating into the wrong environment. Since I keep the /home on a separate partition no big fuss.

---

### Post by haddog on 2010-03-31
I had no luck upgrading either. Ended up with the desktop version. Restored my system bqack to UNR 9.10 with a clonezilla backup. I do have the UNE 10.04 cd but have not figured out how to upgrade UNR 9.10 with it.

---

### Post by go7Ul1ai on 2010-03-31
I just upgraded my girlfriends netbook (HP Mini 10) from Karmic to Lucid and everything is working mighty fine :) I upgraded yesterday (if that makes a difference).

---

### Post by haddog on 2010-03-31
> **lee.jarratt said:**
> I just upgraded my girlfriends netbook (HP Mini 10) from Karmic to Lucid and everything is working mighty fine :) I upgraded yesterday (if that makes a difference).

How did you do it? What were the steps you used? You got the Netbook desktop not the standard desktop when you upgraded correct?

---

### Post by xfalcox on 2010-03-31
Same problem here.

HOW TO FIX:

After reboot in the login screen you need to select Netbook Edition where is writen Gnome.

---

### Post by nanog on 2010-03-31
The upgrade worked for me on a dell mini 9. I did the normal update-manaager -d upgrade.

---

### Post by go7Ul1ai on 2010-03-31
> **haddog said:**
> How did you do it? What were the steps you used? You got the Netbook desktop not the standard desktop when you upgraded correct?

I did the usual Alt+F2 to bring up the Run window, I then entered in "update-manager -d" (without quotes) and ran through that update process. It was running the Karmic Ubuntu Netbook Remix and after the upgrade the netbook interface is still there and running fine.

---

### Post by haddog on 2010-04-01
> **lee.jarratt said:**
> I did the usual Alt+F2 to bring up the Run window, I then entered in "update-manager -d" (without quotes) and ran through that update process. It was running the Karmic Ubuntu Netbook Remix and after the upgrade the netbook interface is still there and running fine.

Interesting. I used the same procedure and did not get the netbook interface after reboot but a "slighty modified" standard gnome desktop.Oh well. I went ahead and did a clean install. Thanks for the reply.

---

### Post by haddog on 2010-04-01
Post tips to my new thread entitled [UNE 10.04 Did You Know?]("http://ubuntuforums.org/showthread.php?t=1444735")

---

### Post by erasrhed42 on 2010-04-01
The info on the 'download beta 1' page had me confused. The only Netbook Remix listed there is paired with the Kubuntu ISO page. While the Kubuntu Netbook Remix looks nice, it's not what I wanted.

From digging through forums, I gather that UNR has been renamed UNE - Ubuntu Netbook Edition. And from haddog's "UNR/UNE 10.04 Did You Know?" thread and this one, it seems the regular Ubuntu Desktop is also the Netbook Edition, with the option in the GDM login screen to choose which you want to see. 

How can we get this better explained on the download page?

So... I'm now going to give the 'update-manager -d' a spin on my Dell Mini 9 to upgrade from 9.10. Let's see how this goes.  :D

---

### Post by haddog on 2010-04-02
> **erasrhed42 said:**
> The info on the 'download beta 1' page had me confused. The only Netbook Remix listed there is paired with the Kubuntu ISO page. While the Kubuntu Netbook Remix looks nice, it's not what I wanted.

From digging through forums, I gather that UNR has been renamed UNE - Ubuntu Netbook Edition. And from haddog's "UNR/UNE 10.04 Did You Know?" thread and this one, it seems the regular Ubuntu Desktop is also the Netbook Edition, with the option in the GDM login screen to choose which you want to see. 

How can we get this better explained on the download page?

So... I'm now going to give the 'update-manager -d' a spin on my Dell Mini 9 to upgrade from 9.10. Let's see how this goes.  :D
 
I hear ya erasrhed42, it is confusing. There is an ISO for Ubuntu Netbook Edition/UNE, the replacement for UNR. You have to go to the Ubuntu Desktop and Server link:

[http://releases.ubuntu.com/releases/10.04/](http://releases.ubuntu.com/releases/10.04/)

Then scroll down to the section that says Netbook Live CD. you will see a link that says PC (Intel x86) netbook live CD. This will get you the latest Ubuntu Netbook CD ISO. I gave up on ugrading UNR 9.10 to UNE 10.04 Beta1 via CD and did a clean install.

Please post how your upgrade goes.

---

### Post by erasrhed42 on 2010-04-09
I'm happy to report back that the upgrade went smoothly using the update-manager -d. No problems at all with the process. The only issues I ran into were due to available disk space and system speed on this Mini 9 (16 Gb model).

The upgrade took a while figuring out what needed installing, then told me I needed to find more disk space. After I un-installed some bigger apps and removed files it eventually continued to the actual installation. After the reboot, it went right to the netbook login screen without my having to do anything extra.

So far, so good, and no complaints with the upgrade. Now I just need to spend more time breaking it in fully. Too many other demanding computers, not enough time.  :)

---

### Post by cariboo on 2010-04-09
You can report problems with web pages on launchpad, just like you would with any other bug.

---

