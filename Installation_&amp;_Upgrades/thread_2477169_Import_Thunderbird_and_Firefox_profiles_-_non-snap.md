---
title: "Import Thunderbird and Firefox profiles - non-snap PC to snap PC"
date: 2022-07-16
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2022-07-16
I want to import TB and FF profiles from a PC running 18.04 to a PC with a fresh install of 22.04.  

A few years ago I imported both profiles successfully from a 16.04 PC to an 18.04 PC but that was before snap.  Snap is new to me.

**THUNDERBIRD**
On the 22.04 PC I found the TB profile: Home/ .thunderbird/ xxxxxxxx.default.  Does the path mean that TB is not yet part of snap, and I can import the old TB profile just like in the past?  All I had to do last time was go to Home, View Hidden Files, find the old profile, and copy it to a thumb drive.  Then go to the "new" PC, delete or re-name the existing profile, then paste the imported profile into the ".thunderbird" folder.  Reboot the PC and Thunderbird came up on the new computer just like the old one.  Pretty easy.

**FIREFOX**
On the 22.04 PC the FF profile was found inside the snap folder: Home/snap/firefox/common/.mozilla/firefox/xxxxxxxx.default.  How does snap complicate the process of importing the old FF profile to the new PC?  Now that I found where the Firefox profile is stored (inside the snap folder) can I just copy/paste as described above for TB?  Or is it more complicated than that?

---

### Post by #&amp;thj^% on 2022-07-16
copying has always worked for me.
Profile folders are located in ~/.thunderbird//. If you use a third-party build from Debian or Ubuntu, go to ~/.mozilla-thunderbird.

After you locate your Profile folder, back up or move your Mozilla Thunderbird profile, or archive specific folders.

Mozilla Thunderbird saves your personal information in a set of files called a Profile. The Profile houses local mail, copies of messages that reside on the mail server, and changes made to the Thunderbird account settings or toolbar. Thunderbird stores Profile files and program files separately, so you can uninstall Thunderbird without losing your messages and settings. If something goes wrong with a Thunderbird update, your information will still be available.
So maybe a back-up of both complete folders, will save some time and lost settings.

---

### Post by Bartender on 2022-07-16
New problem -
I'm trying to copy/paste the TB profile from the 18.04 PC to a 4GB thumb drive.  The profile size is about 1.5 GB.
When trying to Copy/paste, I got an error message.

Error while copying "lock".

Under more details, it says "File system does not support symbolic links".

TB was not running when I tried the copy/paste.  This little project is going sideways on me!

---

### Post by #&amp;thj^% on 2022-07-16
OMG you got to love it right? This is a Ubuntu/Debian quirk... I had forgot that.
But you can use that profile but you will have to tell Thunderbird which one to use.
If you go to Thunderbird  right click on the top bar and tell it to add menu bar the under the help tab, >> go More troubleshooting information, scroll down the window that comes up and select profiles.

---

### Post by Bartender on 2022-07-16
I took very careful notes when I last imported the TB profile to a newer version of Ubuntu.  I'm sure I copied the profile to a thumb drive then.  So why not now??  I googled around and some folks are saying FAT32 doesn't handle symbolic links but NTFS does.  Maybe I'll try plugging in a dock and hdd.  See what happens.

OK, interesting.  Plugged in a dock and a blank NTFS HDD.  The TB profile copied to the dock w/out any error messages.  Then I reformatted the HDD to EXT4.  Copy/pasted the TB profile again.  No error messages.  Does that mean I can bring the profile over to the 22.04 PC and replace the existing profile?  

I don't understand your instructions re: the menu bar & help tab.  I can't tell TB which profile to use until I can copy the old profile into the 22.04 PC so it's starting to sound Catch-22.

---

### Post by #&amp;thj^% on 2022-07-16
Not at all a catch-22, just to be clear, and I know you already understand, but see screenshot.
Then point it to your thumbdrive where the profile is.
It works I promise. ;)

---

### Post by Bartender on 2022-07-16
Weird.  Finally got the old profile to the new PC.  Added a few letters to the existing profile, the one I didn't want to use.   Started TB.  It came up with the new, nearly empty profile.  Not the one I wanted.  I temporarily moved the new profile off the PC entirely and it STILL came up looking just like a new TB install.  No sign of the old profile I wanted to use.  Brought the new profile back over since it didn't seem to make any difference.  I went into troubleshooting and tried to find a place to pick profiles.

BTW - This brings up another mystery.  When I set up TB on the new 22.04 PC it asked for name, email, and password.  I'd just recently been forced to go to OAuth instead of my old passwords.  Folks who helped me do this said to erase the old passwords from Password Mgr. once I got OAuth to work.  So which password did TB want when setting up the new account?  I found a copy of the old password and typed it in.  That worked to get TB started on the new PC.  I am now completely mystified as to OAuth.

---

### Post by #&amp;thj^% on 2022-07-16
Gmail just changed that a few months back, now all outside of some browsers is considered a third party UN-trusted appliction, thus>> **OAuth**
Big Brother anyone? :)

---

### Post by TheFu on 2022-07-16
Don't use gmail and your OAuth issues will go away.

Snap packages have been breaking integrations between firefox and other programs since 22.04 was released. Be prepared for that.  Don't expect clicking "mailto:" links on websites to work and don't expect "https://" links in email to open in firefox.  Of course, nobody should be clicking on either or any links in email programs the last 15 yrs, so this shouldn't be a problem today.

---

### Post by #&amp;thj^% on 2022-07-16
> **TheFu said:**
> Don't use gmail and your OAuth issues will go away.


:lolflag:
Ah yes in a perfect world...right? ;)

---

### Post by Bartender on 2022-07-16
1fallen -
I missed your latest message while screwing around.
I'm onboard with your directions.  I can get to "Help", then "More troubleshooting", then I can click on "Open Directory".  That opens the xxxxxxxx.default-release folder.  It does not open to either profile.  Gotta go back a level to see the profiles.  I tried making it use the imported profile but no joy.

---

### Post by TheFu on 2022-07-16
> **1fallen said:**
> :lolflag:
Ah yes in a perfect world...right? ;)

I suppose. It was the real world for me.  When google mandated gmail use oauth on June 1, 2022, I stopped using gmail.  Not hard at all. No more oauth issues at all.
Life is too short to screw around with companies trying to fire themselves. There are plenty of options that can be used easily without oauth hoops.

---

### Post by #&amp;thj^% on 2022-07-16
> **TheFu said:**
> 
Life is too short to screw around **with companies trying to fire themselves.** .
Indeed! It is getting fierce out there anymore.
I'm not sure people really want easy though, and well said, >>it's easy to switch. Life is easy again.

---

### Post by #&amp;thj^% on 2022-07-16
> **Bartender said:**
>  I tried making it use the imported profile but no joy.

Sorry TheFu and I was poking a bit of fun at the Corporate World, so keep us updated, I'll check back.

---

### Post by bcschmerker on 2022-07-18
**I'm a Google user as well as a once and future ubuntu sysadmin.**  The jccwc-projection project hit a setback March 2022, but I'm planning on 22.04.2-LTS when I get a YESTON® RX550-4DG5-LP into the EL1210; snap will force new profiles anyways, as the user profiles on the EL1210 destined for Church were incomplete when the 1210 was last up.  (mozilla® Firefox® defaulted to WebRender (Software) due to different-gen GPUs from nVIDIA®, viz., the planar C77 and the add-on GF119, on the same device.)  Got specific apps on a |&#862;&#863;1&#863;&#8314;® DE2118 (forced upgrade from a KYOCERA® C6530n) and an &#593;lc&#593;tel® 9032Z (new tablet), both running android 11 as of 18 July 2022.  Hopefully I can convert the ASUS® CM1630 as upgraded to 22.04.x-LTS as soon as I build and install a new Win 11 tower; LinUX has a history of reliable support for older hardware.

---

