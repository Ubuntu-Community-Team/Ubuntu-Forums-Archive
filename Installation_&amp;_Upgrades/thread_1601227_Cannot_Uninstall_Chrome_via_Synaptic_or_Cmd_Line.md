---
title: "Cannot Uninstall Chrome via Synaptic or Cmd Line"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by onaridge on 2010-10-20
I found the solved thread on this and nothing helped me there. I cannot uninstall Chrome. Being a newb and a big chrome user I did a no-no and went out and grabbed it right away from the net (not knowing about the safety issues or much about Ubuntu at that time)rather than using the pkg on my system. Now I can't find it to uninstall it and using the command line results in no pkg found. I then stopped using it and installed the Chromium version and am using that for now but I hate loose ends and wonder if it's risky having it on my system. It would be a good learning experience too to find out how to uninstall it. Synaptic doesn't show anything either.

---

### Post by oregonbob on 2010-10-20
What safety issues? What is so dangerous it shouldn't be on your system even if you choose not to use it?

If you feel that strongly, you can remote it from /opt/google/chrome. That is where it lives.

---

### Post by onaridge on 2010-10-20
The fella that installed Lucid Lynx for me told me that Chrome was dangerous if I didn't get it from one of the repositories. This was after I installed it of course. How do I find the OPT directory?

How easy is it anyway to get malicious scripts, viruses and spyware as compared to Windows. I didn't think it was which is why I switched from Windows.

---

### Post by oregonbob on 2010-10-20
Where did you get Chrome? If you downloaded it from Google you don't need to worry. I don't agree that Google Chrome is dangerous. In fact I feel safer having the Google name behind my browser and I know they do special safety stuff like running blacklists, tracking malware sites, etc. If you downloaded it from some unknown site then it could be dangerous. in general browsing in linux is much safer than Windows because most malware expects a Windows system. [http://voices.washingtonpost.com/securityfix/2009/10/e-banking_on_a_locked_down_non.html](http://voices.washingtonpost.com/securityfix/2009/10/e-banking_on_a_locked_down_non.html)

Try this command from a terminal session: 
sudo dpkg --get-selections | grep -i chrome

Does it display any lines?

---

### Post by onaridge on 2010-10-20
The lines were:

google-chrome-beta             install
xserver-xorg-video-open-chrome     install

Where do repository installs go as opposed to non rep installs which I guess go to the OPT folder.

---

### Post by onaridge on 2010-10-20
Oh and I got it from the Google site

---

### Post by TBABill on 2010-10-20
Just for future reference, the only items you will find in Synaptic or the Ubuntu Software Center are applications you can download from the repositories. Chrome is not contained because it is proprietary software owned by Google. It is made from the open source Chromium browser, which IS in the repositories. I like Chromium better myself, but that's preference only. If you had installed Chromium and wanted to remove it, then you just go to Synaptic and mark it for removal, then click apply.

---

### Post by onaridge on 2010-10-20
yes thanks I understand that part now but where do the other programs go...always to the OPT folder? I found the Chrome files there but I don't know how to remove them. I can't drag or right click on them. I am having the same problem with screenlets. When I click on "get more screenlets", I don't understand how to install or activate them despite the instructions. If they don't appear on the screenlet panel, how to do you manage them?

---

### Post by oregonbob on 2010-10-21
> **TBABill said:**
> Just for future reference, the only items you will find in Synaptic or the Ubuntu Software Center are applications you can download from the repositories. Chrome is not contained because it is proprietary software owned by Google. It is made from the open source Chromium browser, which IS in the repositories. I like Chromium better myself, but that's preference only. If you had installed Chromium and wanted to remove it, then you just go to Synaptic and mark it for removal, then click apply.

Chrome is not proprietary software "owned by Google". It is open source Google's port of Chromium. Normally it is better than Chromium but just lately I've had Chrome problems related to flash. Chrome has some safety features Chromium lacks. If the original poster downloaded from Google.com, the software is totally safe and no need to remove it. But if you want to remove it, have you tried command:

sudo apt-get remove google-chrome-beta

or

apt-get remove --force-yes google-chrome-beta

If it fails, tell us what it says.

You fear and urge to remove chrome is unfounded. Whoever told you that it is dangerous is full of crap.

---

### Post by onaridge on 2010-10-21
1st command: couldn't find package Google

2nd command: E: could not open lock file /var/lib/dpkg/lock - open (13 permission denied)

E: unable to lock the administration directory (var/lib/dpkg/) are you root?

---

### Post by oregonbob on 2010-10-21
(See next message below) I can't figure out how to delete this entry.

---

### Post by oregonbob on 2010-10-21
My typo on the commands, both must start with "sudo" as in

sudo apt-get remove google-chrome-beta

or

sudo apt-get remove --force-yes google-chrome-beta

---

