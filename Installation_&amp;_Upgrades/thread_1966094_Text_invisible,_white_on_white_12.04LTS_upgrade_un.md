---
title: "Text invisible, white on white: 12.04LTS upgrade unuseable"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by bogan on 2012-04-26
re **INVISIBLE TEXT **after 12.04 upgrade from 11.10

After a remarkably trouble-free Update Manager up-grade to the newly released 12.04  3.2.0-23-generic - the download estimated at 38 minutes took just under an hour, and Installation estimated at 3 Hours 20 minutes, also took just under an hour - the only fault was a message just before the log-in screen, saying: "could not write bytes: broken pipe".

After reinstalling the nvidia 295.33 driver using: ```
nvidia-installer -f 
```the only installation problem was the Grub menu - and Grub Customizer - had duplicate entries that I could not delete, only hide.

Virtually all my settings and applications survived OK, except for 'Ubuntu-Tweak' which is not shown in Ubuntu Software center.

That is the GOOD news.

[COLOR=Red]**However, there is one major difficulty that makes it virtually unusable!! **[/COLOR]The text display in most windows varies from off-white on a light gray background - just readable - to white on white, or gray on gray - totally invisible.

All the settings windows in System Settings and CCSM, for instance, or the Home folder display, are only readable after Mouse clicking on them to select.

In Gedit, I am typing this after using Edit>Preferences to change to a near black background so the white text is visible; WHILST TO SAVE THE FILE I HAD TO TYPE ITS NAME COMPLETELY BLIND.

Luckily, I have the Classic-Indicator and its display is white on black, so I was able to search through all the configuration preferences, but was unable to find anything other than for Gedit.

Surely this can not be intended, yet I have seen no mention of such things in the Ubuntu +1 testers forum.

Will someone please tell me what ought to be obvious; how do I reset the general text colour/background to make things readable??

Hopefully.

Chao!, bogan.

Edit: PS. I did have one " Sorry 12.04 LTS has encountered an error" message.

---

### Post by cariboo on 2012-04-26
Open a terminal and type:

```
sudo apt-get -f install
```

it looks like your upgrade didn't finish.

---

### Post by jadtech on 2012-04-26
well even more maybe someone else can answer this I could be wrong but 
kernel  3.2.0-23 is 12.04 beta 2 the last beta kernel ..

maybe just because I was using beta but the kernel I installed was  3.2.0-24

---

### Post by bogan on 2012-04-27
Hi!.** cariboo907**,

Thanks for your reply.

When the initial upgrade was complete - there were no error messages - I rebooted, fixed the video driver and ran Update Manager again, there was only one minor update.

This morning I ran: ```
sudo apt-get update
sudo apt-get upgrade 
```and it installed a few packages, mostly a Firefox upgrade. Another reboot and I ran your code:```
 sudo apt-get -f install
  .....one libcxx file replaced .....
The following packages were automatically installed and are no longer required:
  libunity6 screen-resolution-extra
Use 'apt-get autoremove' to remove them.
.....
 sudo apt-get autoremove
The following packages will be REMOVED
  libunity6 screen-resolution-extra
``` Result: **Still the same 'white on white' text**.

**@jadtech**,

Thanks for your tip, I should have noticed, from 'uname -a', that 3.2.0-23 was dated April 10, whereas 3.2.0-24 is dated April 25.

I re-ran Update Manager - which did not show: "12.04 LTS upgrade available" - and it offered the whole eight 12.04 kernal, image and header files.

Installed them and re-booted. Result: **Still the same 'White on White', **and the "could not write bytes: broken pipe" message is still there.

uname now shows: ```
 uname -a
Linux alan-MS-7318 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i386 GNU/Linux
```Any one got any other ideas ??

Chao!, **bogan**.

---

### Post by bogan on 2012-04-27
Update: Fri /27/04/12 pm.

To eliminate the chance that this 'White on White' is connected with the current problems with nvidia driver 295.xx, I downloaded the biuld-esstential and compiling tools, uninstalled & remove purged the 295.33 driver and installed 290.10.

Result: Still the same as before, no change.

There is some good news amongst the bad: my  Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter has connected and worked immediately, every reboot - so far - and even reconnects on recover from Suspend. Things it never did reliably right back to Ubuntu 9.1.

The Desktop, Plymouth log-in window and Terminal windows have text/backgrounds that are legible: Firefox and LibreOffice are black on white or near-white, so things are not totally unusable, but very difficult: Gedit is the only one that I have been able to find Preferences to permit changing the background color.

Can anyone tell me if there are 'Themes' that change window backgounds or text colour??

Chao!, bogan.

---

### Post by bogan on 2012-04-27
Hi!, **All**.

Posted by **bogan**: > Can anyone tell me if there are 'Themes' that change window backgounds or text colour??Answering my own query: I added the tualatrix ppa and installed Ubuntu-Tweak v7.0.

Altering the Gtk theme to 'Radiance' and the Window theme to 'Dust Sand', gave me a good compromise between visibility and contrast.

Result: Problem Solved !!
EDIT: ** You can also do the same thing in Dash>Advanced Settings>Theme.**
                                              :lolflag:
Chao!, **bogan**.

---

