---
title: "Installation Resulted in Boot and Live CD Boot or any Rescue Boot  Failing"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by jonhosseini on 2012-06-04
I am a neewbie so please be patient with me. I succesfullly installed Ubuntu 12.04 alongside a dead windows vista (blue screen of death) installation and was very proud of myself. Was able to get all/most of my data off the drive onto thumbdrives using ubuntu...and was thrilled. Confident enough that i no longer had any use for Windows Vista... i initiated install of ubuntu 12.04 again, selecting the installation option to replace everything on the hard drive.   Installation was about 80% complete and then just 'hung' for about 2 hours saying 'copying files'.... had not choice but to abort installation. Tried to initiate install again but now Live Ubuntu 12.04 CD is not recognised. get blank screen saying "Missing operating system. Operating System Not Found"   Boot sequence is correct for CD Rom Boot, tried SuperGrub2 disk ...not recognised, same message, tried Rescatux Rescue CD as cd and as disk image on Thumb Drive... always same message "Operating System Not Found"  
Please help me recover from this....  I tasted the joy and freedom of Ubuntu and when i wanted to go all the way as ubuntu only... i hit this....

---

### Post by oldfred on 2012-06-04
Some have had BIOS issues where the BIOS just seems to lockup.

If a Desktop totally power off for a minute, if a laptop power down and remove battery so it does totally power down.

Then see if CD can be selected in BIOS again. Run test to confirm that CD is good, it may have gotten scratched or something. 

I used to burn a lot of CDs when I did new installs, but now use USB flash drives as I like to have several repair ISO as well as the install ISO.

---

### Post by dino99 on 2012-06-04
i suppose you dont made partionning with boot flag

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

but if you set the bios to boot on cd/dvd, then you might boot on recovery mode to perform a check and continue the installation.

---

### Post by jonhosseini on 2012-06-04
thank you oldred... tried shutting down and removing battery no joy..

---

### Post by jonhosseini on 2012-06-04
dino 99 ..how can i work on the partitions etc. when i only get a blank screen... no live cd or rescue cd is recognized to get anywhere into anything that will allow me work on anything... please advise ..is there some machine language way of working on it? if so can someone walk me through it....

---

### Post by dino99 on 2012-06-04
> **jonhosseini said:**
> dino 99 ..how can i work on the partitions etc. when i only get a blank screen... no live cd or rescue cd is recognized to get anywhere into anything that will allow me work on anything... please advise ..is there some machine language way of working on it? if so can someone walk me through it....

the next step is to boot with some  "option" on the boot line, first try with nomodeset or noacpi

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by jonhosseini on 2012-06-04
> **dino99 said:**
> the next step is to boot with some  "option" on the boot line, first try with nomodeset or noacpi

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

i followed the directions provided in the link above...however nothing from the live cd comes up... i am using an acer aspire5570 and it previously recognized the live cd and now nothing... tried holding down various keys such as F1, and F12 while restarting ..none of them took me to the options menu ..just finally repeated "operating system not found".

This is the same live cd that was previously used and successfully recognized on the same machine just a few hours prior. More suggestions...? the engineer in me does not believe that there is no way to access and correct whatever is going on between the bios, the hard drive, and the cd rom, live cd.

thank you for your help so far...

---

### Post by strask on 2012-06-04
If you have any USB thumb drives plugged in, remove them and try rebooting off the ubuntu CD.

---

### Post by jonhosseini on 2012-06-04
> **strask said:**
> If you have any USB thumb drives plugged in, remove them and try rebooting off the ubuntu CD.

hi trask thank you... no usb's plugged in tried that....

---

### Post by oldfred on 2012-06-04
Besides BIOS boot order, do you have a one time boot key (f12 on my system)?

 If you keep getting no boot it is not reading CD or USB as bootable or seeing them correctly  or not going to them first. Some Dell's required both BIOS boot order and one time boot key to get anything other than hard drive to boot. 
Then it goes to hard drive and if it fails then it gives error message.

Reverify that CD or USB is bootable by trying in any other system. Friend, neighbor, work computer, whatever you can use to test to see that CD is still ok. After running the on CD test if you can.

---

### Post by strask on 2012-06-04
> **jonhosseini said:**
> tried holding down various keys such as F1, and F12 while restarting ..none of them took me to the options menu

I just found this in the manual for your aspire system: To activate the BIOS utility, press <F2> during the POST; while the notebook PC logo is being displayed

---

### Post by jonhosseini on 2012-06-04
> **oldfred said:**
> Besides BIOS boot order, do you have a one time boot key (f12 on my system)?

 If you keep getting no boot it is not reading CD or USB as bootable or seeing them correctly  or not going to them first. Some Dell's required both BIOS boot order and one time boot key to get anything other than hard drive to boot. 
Then it goes to hard drive and if it fails then it gives error message.

Reverify that CD or USB is bootable by trying in any other system. Friend, neighbor, work computer, whatever you can use to test to see that CD is still ok. After running the on CD test if you can.

tried f12 one time boot key, no joy

tested cd on a separate desktop computer and it is booting ok...    :-(   but determined.... :-)

---

### Post by wilee-nilee on 2012-06-04
From the manual.

Press f2 to enter setup. The default parameter of F12 Boot Menu is set to &#8220;disabled&#8221;. If you want to change
boot device without entering BIOS Setup Utility, please set the parameter to &#8220;enabled&#8221;.

Press <F12> during POST to enter multi-boot menu. In this menu, user can change boot device without
entering BIOS SETUP Utility.


Google search 3rd choice.
[https://www.google.com/search?hl=en&output=search&sclient=psy-ab&q=acer+aspire5570+per+session+boot+menu&btnG=&gbv=1&sei=RujMT4HqLqOc2AXlydDfDQ](https://www.google.com/search?hl=en&output=search&sclient=psy-ab&q=acer+aspire5570+per+session+boot+menu&btnG=&gbv=1&sei=RujMT4HqLqOc2AXlydDfDQ)

---

### Post by flemur13013 on 2012-06-04
When you get into BIOS, check everything, especially the boot and CD options.  If you don't find anything that looks like it might be preventing you from booting from a CD (and that you therefore change!), try "reset to defaults", which should be in there somewhere.

---

### Post by jonhosseini on 2012-06-04
> **strask said:**
> I just found this in the manual for your aspire system: To activate the BIOS utility, press <F2> during the POST; while the notebook PC logo is being displayed

thank you strask - i have been working within the bios utility.

---

### Post by jonhosseini on 2012-06-04
> **flemur13013 said:**
> When you get into BIOS, check everything, especially the boot and CD options.  If you don't find anything that looks like it might be preventing you from booting from a CD (and that you therefore change!), try "reset to defaults", which should be in there somewhere.

thanks tried reset to defaults... no joy

left field question for all out there (2 questions)... it seems something has changed between the cmos and the cd rom...  it seems it has nothing to do with the hard drive.

q1. during ubuntu install is anything done to or written to cmos...

q2. if so or even if not... would removal of the cmos battery and reenergizing after say 30 minutes do anything different in the way of reverting back to original settings in a way that using the bios utility to "reset all bios defaults" would not?

---

### Post by wilee-nilee on 2012-06-04
> **jonhosseini said:**
> thank you strask - i have been working within the bios utility.

Note post 13, download the manual, hit ctrl-f type in f12 the hit enter twice I think, and in the second chapter is my quote.

When all all fails looking up the manual is rather helpful. ;)

I have an acer as well different model I had to unlock the f12 key as well in the bios.

---

### Post by jonhosseini on 2012-06-04
> **flemur13013 said:**
> When you get into BIOS, check everything, especially the boot and CD options.  If you don't find anything that looks like it might be preventing you from booting from a CD (and that you therefore change!), try "reset to defaults", which should be in there somewhere.

thanks. did this... see my note below in reply to willi nillie...

---

### Post by jonhosseini on 2012-06-04
> **wilee-nilee said:**
> Note post 13, download the manual, hit ctrl-f type in f12 the hit enter twice I think, and in the second chapter is my quote.

When all all fails looking up the manual is rather helpful. ;)

I have an acer as well different model I had to unlock the f12 key as well in the bios.
thank you for pointing me to the service manual... i was already able to get to the bios utility and the f12 option... you make reference to "ctrl-f" i don't see that anywhere in the manual ...what does that do... could you point me to a specific page that you are seeing? 

separately the manual is very helpful in pinpointint the cmos jumper position on the motherboard... do you have any thoughts on my posting #16?

---

### Post by wilee-nilee on 2012-06-04
> **jonhosseini said:**
> thank you for pointing me to the service manual... i was already able to get to the bios utility and the f12 option... you make reference to "ctrl-f" i don't see that anywhere in the manual ...what does that do... could you point me to a specific page that you are seeing? 

separately the manual is very helpful in pinpointint the cmos jumper position on the motherboard... do you have any thoughts on my posting #16?

Crtl-f brings up a search box.

One of the easier ways to find something specific.

---

