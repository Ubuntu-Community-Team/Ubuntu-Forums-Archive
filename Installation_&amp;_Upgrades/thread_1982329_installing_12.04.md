---
title: "installing 12.04"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by leilton on 2012-05-18
I cannot believe i am the only person who has this problem, but have searched forums with no luck.

Have now downloaded 12.04 from 6 different sites, burnt to six different disc (just in case), and when I try to install, get to same point each time and each time end up with a blank screen and a cursor flashing away like mad in the left hand top corner.

Have 11.04 already installed, and know can do upgrade, but advised best to do new install, but  HOW?

Surely even I cannot be that stupid that I'm missing something?

Any help much appreciated

---

### Post by jadtech on 2012-05-18
> **leilton said:**
> I cannot believe i am the only person who has this problem, but have searched forums with no luck.

Have now downloaded 12.04 from 6 different sites, burnt to six different disc (just in case), and when I try to install, get to same point each time and each time end up with a blank screen and a cursor flashing away like mad in the left hand top corner.

Have 11.04 already installed, and know can do upgrade, but advised best to do new install, but  HOW?

Surely even I cannot be that stupid that I'm missing something?

Any help much appreciated

it doesn't haveto do with the disk being bad  it has to do with the fact you  need to set a boot modification 

such as nomodeset

when you start the boot when you see the boot menu  press f6 select the nomodeset option, try each option till  it boots and keep in mind the live cd take time to probe and  boot completely it not quick like booting  from Hard drive..

it can take more then several mins to boot  to live cd, the black screeen with the cursor  at the top is a normal part of  bootup if it hangs on forever and all progress stops this is an issue  that might require a boot modification  it stuck tryingto find one or another driver or locked up  for some other reason ..

for a faster go with live cd once you do get booted  and to test ubuntu you can load Gparted and if you have already allocated free space on the drive for ubuntu  you can make the swap partition first it woill automatically be mounted and speed up the live cd :) 

if you still have issues with the CD try bootable usb version of the ISO or the mini ISO which is a text version of the installer ..

---

### Post by leilton on 2012-05-18
> **jadtech said:**
> it doesn't haveto do with the disk being bad  it has to do with the fact you  need to set a boot modification 

such as nomodeset

when you start the boot when you see the boot menu  press f6 select the nomodeset option, try each option till  it boots and keep in mind the live cd take time to probe and  boot completely it not quick like booting  from Hard drive..

it can take more then several mins to boot  to live cd, the black screeen with the cursor  at the top is a normal part of  bootup if it hangs on forever and all progress stops this is an issue  that might require a boot modification  it stuck tryingto find one or another driver or locked up  for some other reason ..

for a faster go with live cd once you do get booted  and to test ubuntu you can load Gparted and if you have already allocated free space on the drive for ubuntu  you can make the swap partition first it woill automatically be mounted and speed up the live cd :) 

if you still have issues with the CD try bootable usb version of the ISO or the mini ISO which is a text version of the installer ..

Jadtech:

You Sir are a gentleman.   Will be giving that a go as soon as my wife lets me back on to this laptop.   To be honest thought it would be a couple of hours before got response.

I did, I see, neglect to say, that before get the cursor, get asked if I want install or try, but whichever I choose still get the dreaded cursor, does that affect your answer in any way?

Thanks a bunch, will let you know how I get on.

---

### Post by jadtech on 2012-05-18
shouldnt change nothing but if you keep having issues  try the other methods also  the ISO when burned is  a bit larger then the average CD  and tends to work  way better burned on a DVD some cds will  reject the few MB over ..

---

### Post by leilton on 2012-05-18
> **jadtech said:**
> shouldnt change nothing but if you keep having issues  try the other methods also  the ISO when burned is  a bit larger then the average CD  and tends to work  way better burned on a DVD some cds will  reject the few MB over ..

Hi jadtech,

Thanks, sorry did not get back quicker, been trying all the options and all the buttons I could think of, and yes I have burnt 12.04 to both a CD and a DVD.

Have now, also, to test that I am not as stupid as I seem to think I must be, tried, (and successfully) to install L Ubuntu and Mubuntu, both 11.10, and no problem, I assume that it is not my laptop that is the problem. Both taken out as not required.

Did at one stage, when trying to install 12.04, get to being told that I did not have driver for Broadcom, (who does), and it locked up there.

Think I'll have another go at finding a download site, and see if any better, although will not hold my breath.

Sorry to have given you so much hassle, thought it would be something simple I was doing wrong.

Thanks for help

---

### Post by jadtech on 2012-05-18
> **leilton said:**
> Hi jadtech,

Thanks, sorry did not get back quicker, been trying all the options and all the buttons I could think of, and yes I have burnt 12.04 to both a CD and a DVD.

Have now, also, to test that I am not as stupid as I seem to think I must be, tried, (and successfully) to install L Ubuntu and Mubuntu, both 11.10, and no problem, I assume that it is not my laptop that is the problem. Both taken out as not required.

Did at one stage, when trying to install 12.04, get to being told that I did not have driver for Broadcom, (who does), and it locked up there.

Think I'll have another go at finding a download site, and see if any better, although will not hold my breath.

Sorry to have given you so much hassle, thought it would be something simple I was doing wrong.

Thanks for help

well there is away around that too I am some what new to all of this myself you can  actually black list that driver for your wireless card how maybe someone else will have to post the details  .. 

you could reinstall 11.10 and try and run upgrade to 12.04 right on-line .. 

another way try to  run the install maybe without internet or wireless connection  maybe run it plug into your router.. 

most likely once its install like with me whenI  install on this HP  the driver will be in the additional drivers list in system settings ready to down load and  active :)

in the mena time I will try to google up the  lines to use to black list this issue to get  the CD booted

---

### Post by jadtech on 2012-05-18
ok I beileve this is the helper you are looking for  , for this bug 

[http://ubuntuforums.org/showpost.php?p=11883375&postcount=6](http://ubuntuforums.org/showpost.php?p=11883375&postcount=6)

not to worry about the issues some of these bugs are common because some hardwaremanufactures wont allow there driver softeware out to open source for development and use  so it can't really be added to there install I guess you can use the drivers you just have to down load them after the fact .. 

many hard core open source people wont use any softeware that  isnt open source so  there is a bit of stuborness on all sides.. 

oddly linux always gets the dirty end of the stick  because hardware drivers have come to be called windows drivers rather then software the runs the wireless either cards video cards and such ..

---

### Post by leilton on 2012-05-19
> **jadtech said:**
> ok I beileve this is the helper you are looking for  , for this bug 

[http://ubuntuforums.org/showpost.php?p=11883375&postcount=6](http://ubuntuforums.org/showpost.php?p=11883375&postcount=6)

not to worry about the issues some of these bugs are common because some hardwaremanufactures wont allow there driver softeware out to open source for development and use  so it can't really be added to there install I guess you can use the drivers you just have to down load them after the fact .. 

many hard core open source people wont use any softeware that  isnt open source so  there is a bit of stuborness on all sides.. 

oddly linux always gets the dirty end of the stick  because hardware drivers have come to be called windows drivers rather then software the runs the wireless either cards video cards and such ..

And all of this to get an updated version of Ubuntu, which has taken  them 6 months, so that you need to do all the above just to get back to  basically where you were before they messed about.

I left Windows because they would not leave well alone.

Still waiting to be told why, when I cannot load (only get cursor),  12.04 I have no problem installing, but don't want. downloaded and burnt  to disc, L, M and X Ubuntu.

Going to try and find another version (if that’s the word), of Linux,  Ubuntu can then play around as much as they like, but without me.

---

### Post by darkod on 2012-05-19
I didn't see mentioned specifically in your replies whether you tried the nomodeset parameter or not?

That is usually the solution for black screen with blinking cursor. Video issue.

The b43 firmware bug is a different thing and if that's affecting you you will need both parameters to boot and install.

So, both nomodeset and b43.blacklist=yes.

---

### Post by leilton on 2012-05-20
> **darkod said:**
> I didn't see mentioned specifically in your replies whether you tried the nomodeset parameter or not?

That is usually the solution for black screen with blinking cursor. Video issue.

The b43 firmware bug is a different thing and if that's affecting you you will need both parameters to boot and install.

So, both nomodeset and b43.blacklist=yes.

Thank you.

But did follow advise from jedtech, and started off with f6 and worked my way thru all other mentioned, all to no avail.

Not sure what fiddling with b43 will prove, get same message with the versions mentioned below, and know how to deal with them, so have not waded through masses of paper.

My question still remains unanswered, why does this not happen when I install Ubuntu 11.20, L,M and X Ubuntu,(all of which load with no problem what so ever).

To my mind Ubuntu seems to have gone backwards.

To add to my problem, and the reason I have given up on trying to load 12.04, is that I now get no further than the blank screen and cursor when I insert the disc.

Going to spend a bit more time going through other versions to see what alternative I'll use.   Before converted to Ubuntu, had Suse, might give that another try.

Anyway thanks for the help and advise.

---

### Post by darkod on 2012-05-20
I mentioned the b43 bug in case you are affected by it, I don't know if you are for sure.

If the nomodeset didn't help, it might be an issue with something else, not the video card.

If you want to troubleshoot it, use Esc again during boot to load the main menu, and in the boot options delete the 'quiet splash' parameters. You can also add nomodeset here, to make sure it will use the option. Sometimes using the F6 can be misleading if you think you selected it but you didn't. Then boot with the Try Ubuntu option from the menu.

That will try to load it in text mode and you can usually see where it gets stuck. Watch out for any errors reported before it gets stuck. Usually that shows where is the problem.

A newer version of any OS is not 100% backwards compatible. Just because something worked in 11.10 it doesn't mean it will be working in 12.04. Usually it does. I understand your frustration, but developing an OS is not an easy job either, especially since I ma not sure how much help they get from hardware manufacturers.

For example, I had an old usb wi-fi adapter that worked in XP but later didn't work in win7. Why? The manufacturer never developed drivers for it because they wanted to stop manufacturing it and never bothered with win7 drivers. So, a component that worked just fine in XP couldn't work in win7.

And note that we are talking about windows, not linux. For windows usually manufacturers make drivers long before the OS is released, give them to MS to implement them, and then it looks like windows supports everything out of the box. :) If they do the same with linux, it would be a similar situation... But we can't break the MS grip on the market, can we?

---

