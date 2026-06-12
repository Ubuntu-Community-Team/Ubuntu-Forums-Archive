---
title: "How to upgrade from Maverick 10.10?"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2012-12-27
Do I have to go to System-Administration-Update Manager and click on Upgrade to upgrade to 11.04, or can I directly install 12.10 from the DVD?

Will I loose my documents in the process? I never upgraded from an already installed Ubuntu.

Thanks

---

### Post by cybrsaylr on 2012-12-29
I always do a clean installs for upgrading to newer Ubuntu versions.
It seems there are less problems this way. 

Yes you will lose your old 11.04 folders but what I do to save them is, move and save those old 11.04 files, or the whole Home folder, to another external drive, partition, flash drive, etc. Then copy them over to your new 12.10 install if needed.

---

### Post by rajhanschinmay on 2012-12-29
You can do direct upgrade.

Go to respositories in synaptic, select
server from US on first tab.
If you want to upgrade to 12.10 then select normal releases.
If you want to upgrade to 12.04, then select LTS releases only.

Then reload the updates 2 times.
Then select all updates. Apply them and restart once.
Then use the command:
sudo apt-get dist-upgrade

This will do upgrade to either 12.04 or 12.10.

Now 12.04 is a stable LTS version which will have support till 2017.
But 12.10 is normal release which will have support till 2014 only. After that u need to again upgrade. so I suggest u to upgrade to 12.04 version only.
12.04 version will upgrade to 12.04.1, 12.04.2 etc in subsequent years.

Thank you.

---

### Post by Wim Sturkenboom on 2012-12-29
@rajhanschinmay
are you sure about that. As far as I know,
1)
You have to do every single upgrade. So 10.10 -> 11.04 -> 11.10 -> 12.04 -> 12.10. One probably will also battle to get the repositories sorted out as the no longer exist (archived somewhere)
2)
As 10.10 is not an LTS release, you first have to upgrade the difficult way (see above) to 12.04

@rva1945
Specially because you are far behind on this machine, a clean install of 12.04 or 12.10 might be the best way.

---

### Post by rajhanschinmay on 2012-12-29
[@Wim Sturkenboom]("http://ubuntuforums.org/member.php?u=5214") 				 				 			

I think it may be possible.
But I am not sure about upgrading from Ubuntu 10.10 to Ubuntu 12.04.

But from Ubuntu 10.04, it is possible.


[@rva1945]("http://ubuntuforums.org/member.php?u=984471")

I suggest you to insert USB bootable flash drive with Ubuntu 12.04 image.
Then when u reach 'what u want to do' screen, 
if it properly detects ur 10.10 version then it will only give u one option called upgrade from 10.10 to 12.04.
or something else option.

If you do not get such option then select 3rd option i.e. something else.
Here give same /, /home and swap spaces as before.
Uncheck the format option. 

What this will do is it will uninstall or remove all the packages which are not compatible or supported with Ubuntu 12.04, and then install or upgrade or update the remaining ones.
This will also install the packages which were not there in earlier version but are present in new version,

So in summary, I think from Ubuntu 10.04, it is possible,
I am not that much sure from 10.10 if it would be possible.

Do let us know if it works.

Thank you.

---

### Post by blackbird34 on 2012-12-29
And whatever you do BACK UP YOUR DATA :D

IMHO a clean install of 12.04 would be much less hassle.

---

### Post by rva1945 on 2012-12-29
> **blackbird34 said:**
> And whatever you do BACK UP YOUR DATA :D

IMHO a clean install of 12.04 would be much less hassle.

Thank you guys!

Now, what do you mean by a clean install?

I downloaded "ubuntu-12.10-desktop-i386.iso", now I guess a should burn a CD and then when booting, select the install option, right?

Or do I have to upgrade from 0.10 -> 11.04 -> 11.10 -> 12.04 using System/Administration/Update manager and then install from the CD?

Of course I will back all my documents up before.

Thanks again,
Robert

---

### Post by fantab on 2012-12-29
> **rva1945 said:**
> Thank you guys!

Now, what do you mean by a clean install?

I downloaded "ubuntu-12.10-desktop-i386.iso", now I guess a should burn a CD and then when booting, select the install option, right?

Yes, that's right. 

If you don't like installing newer versions of Ubuntu regularly (I am assuming that you don't usually upgrade since you haven't since 10.10) then I suggest that you download and install 12.04 since it is supported till 2017. Your copy of 12.10 will run out of support far sooner than 12.04 LTS. Just a thought for you to consider.

Good Luck.

---

### Post by davidtrounce on 2012-12-29
The default upgrade option worked for me in Ubuntu. I moved up to 12.04 without any problems.

---

### Post by rva1945 on 2012-12-29
> **davidtrounce said:**
> The default upgrade option worked for me in Ubuntu. I moved up to 12.04 without any problems.

You mean, without upgrading to versions between 10.10 and 12.04?

---

### Post by cybrsaylr on 2012-12-29
> **rva1945 said:**
> Now, what do you mean by a clean install?

I downloaded "ubuntu-12.10-desktop-i386.iso", now I guess a should burn a CD and then when booting, select the install option, right?

Doing that is a clean install.

When you go to install 12.10. it  will tell you that it sees you have another version of Ubuntu and that installing 12.10 will replace the old version with 12.10 causing all old files and folders to be lost unless you backed them up or saved them on another drive or partition.

This way you don't have to bother going through all the Ubuntu versions between 10.10 through 12.10. 

BTW I still use 64 bit 12.04 because it's LTS and rock solid.

---

### Post by oldos2er on 2012-12-29
> **rva1945 said:**
> I downloaded "ubuntu-12.10-desktop-i386.iso", now I guess a should burn a CD and then when booting, select the install option, right?

12.10 requires a DVD, it's too big to fit on a CD.

---

### Post by rva1945 on 2012-12-30
> **oldos2er said:**
> 12.10 requires a DVD, it's too big to fit on a CD.

OK, I created the CD and it works. I tried it as a Live CD, but to my surprise, when configuring the keyboard, I had only 4 English keayboards to choose from, I use a Latin keyboard. I always install the English versions of the operating systems, is that the problem? Or once Ubuntu 12.04 is installed I will have the same option that I have now in 10.10 (Preferences-Keyboard-Layout-Add)?

---

### Post by davidtrounce on 2012-12-30
> **rva1945 said:**
> You mean, without upgrading to versions between 10.10 and 12.04?

Yes, but, there is always a risk and if you were able to do a clean install once you have backed up that might be preferable. It depends sometimes on what other configuration changes you may have made in your system while using 10.10 - changes which only you know about.

I know that's not altogether helpful. I can appreciate your frustration.

---

### Post by rva1945 on 2012-12-31
Hi, what do you know about an issue in 12.04 with keyboard layout?

I tried the 12.04 Live CD and found that problem: it always "sees" a US keyboard, mine is Latin American. I thought it was related to running a Live CD, but surfing the web I found many people complaining about this issue: "Keyboard layout always resets to US on reboot" in 12.04, and no way to fix it.

I need to upgrade but that problem with the keyboard will be a real pain.

?

---

### Post by rva1945 on 2013-01-01
> **davidtrounce said:**
> Yes, but, there is always a risk and if you were able to do a clean install once you have backed up that might be preferable. It depends sometimes on what other configuration changes you may have made in your system while using 10.10 - changes which only you know about.

I know that's not altogether helpful. I can appreciate your frustration.

SUCCESS!! I installed 12.04 with the option Upgrade from 10.10, now it's running and I didn't loose any document. But where are the installed applications? the Applications menu is gone!

Where is Chrome? Where is VirtualBox? I can see the virtual machines files. Basically, now i don't know how to run the applications I had installed in 10.10

Thanks

---

### Post by oldos2er on 2013-01-01
Chrome is here: [https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

Virtualbox is in the repositories: ```
sudo apt-get update && sudo apt-get install virtualbox
```

---

### Post by rva1945 on 2013-01-01
> **oldos2er said:**
> Chrome is here: [https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

Virtualbox is in the repositories: ```
sudo apt-get update && sudo apt-get install virtualbox
```

Thanks, I know how to get them, but after upgrading to 12.04 they just went missing.

Now, I installed Chrome, and it became available for existing users; then I created a new user but Chrome is not available for the new user. If I try to reinstall it in its session, the Update Manager says it is already installed.

How can I make Chrome and any other application available to new users?

---

### Post by oldos2er on 2013-01-01
> **rva1945 said:**
> Now, I installed Chrome, and it became available for existing users; then I created a new user but Chrome is not available for the new user. 

Interesting question; short answer: I don't know. Try running the executable in a terminal just to see what happens: ```
google-chrome
```

---

