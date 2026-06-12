---
title: "Bios update hell!"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by ddales on 2006-07-12
I would like to update my BIOS on a Dell 9150.  The process is very clear and simple if you have a floppy.  However, my system doesn't have a floppy.  The process is also very simple if you're running windows.  I'm not running windows obviously.

I have downloaded a DOS 6.22 image and burned it to a CD.  I can boot from the CD no problem.

How in the hell do you get the BIOS .exe onto the CD Image so that you can run it after you boot from the CD?  ](*,) 

I have Googled my *** off and getting pissed.  Can someone please help?

I have no Winblows machine available to do the task, only Dapper.

---

### Post by scxtt on 2006-07-12
you can most likely mount the iso in Dapper and add the file to it, unmont the iso, then burn it again ...

---

### Post by spahn on 2006-07-13
I just got a Dell 9150, and i am having probs moving from one OS to another - could i benefit from updating my BIOS?
Did you figure this out?

---

### Post by tseliot on 2006-07-13
> **ddales said:**
> I would like to update my BIOS on a Dell 9150.  The process is very clear and simple if you have a floppy.  However, my system doesn't have a floppy.  The process is also very simple if you're running windows.  I'm not running windows obviously.

I have downloaded a DOS 6.22 image and burned it to a CD.  I can boot from the CD no problem.

How in the hell do you get the BIOS .exe onto the CD Image so that you can run it after you boot from the CD?  ](*,) 

I have Googled my *** off and getting pissed.  Can someone please help?

I have no Winblows machine available to do the task, only Dapper.

You should be able to copy the content of a floppy disk to a USB pen. Copy also the flash utility and the BIOS there.

Then Set the bios to boot from USB devices.

Boot with the USB pen plugged in and you should be able to flash the bios

---

### Post by BoneKracker on 2006-07-13
New machine?  Do you really need to upgrade the BIOS?  

This isn't something to mess with just because there's a newer version available.  Put the wrong version on there and you can end up needing to re-burn the EPROM.  I've seen several people ship their machines back to the factory after diddling around with their BIOS when they didn't even really need to upgrade it.

The USB approach is valid, provided your machine allows you to boot from USB.  Many machines do not.

If not, the simplest fix is probably to borrow the internal floppy drive from another machine, plug it into the motherboard, set the bios to enable booting from it, etc.

---

### Post by ciscosurfer on 2006-12-13
> **ddales said:**
> I would like to update my BIOS on a Dell 9150.  The process is very clear and simple if you have a floppy.  However, my system doesn't have a floppy.  The process is also very simple if you're running windows.  I'm not running windows obviously.

I have downloaded a DOS 6.22 image and burned it to a CD.  I can boot from the CD no problem.

How in the hell do you get the BIOS .exe onto the CD Image so that you can run it after you boot from the CD?  ](*,) 

I have Googled my *** off and getting pissed.  Can someone please help?

I have no Winblows machine available to do the task, only Dapper.If you really feel like you need to update the BIOS, you can check here >> I have written a HOWTO discussing how to flash your BIOS.  You can find it here: [HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789")

---

### Post by gn2 on 2006-12-13
The fundamental question that has to be asked is: 

_Why_ do you want to update the BIOS?

---

### Post by ciscosurfer on 2006-12-13
People update their BIOS' for a variety of reasons, but mainly to improve its functionality.  If I've done my research correctly for the OPs model, then the Dell 9150 BIOS update will do the following and came out on 7/7/06 >>

1. Improve PCIE graphics detection algorithm.
2. Fix memory module detection for SMBIOS.

To the original poster: if you bought this PC after 7/7/06 from Dell, the the newest BIOS will already have been flashed for you.  Otherwise you can try to follow their instructions on [this page]("http://tinyurl.com/ygorlv") to copy over the .EXE to a DOS disk (when searching for the correct BIOS update page, I used the following criteria: XPS/Dimension 400/9150).  If this is incorrect, please go to the Dell web site and enter the appropriate criteria to get the correct page.  If you'd like more detailed instructions, then my [HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789") is just a click away. :-)

---

### Post by gn2 on 2006-12-13
> **ciscosurfer said:**
> People update their BIOS' for a variety of reasons, but mainly to improve its functionality.

But he hasn't said why he "wants" to update it.

He should only do so if there's a reason why he absolutely "needs" to...

I've done many BIOS updates myself, every time I've done so there's been a compelling reason, and it hasn't always gone well.....

> **ciscosurfer said:**
> 
  If I've done my research correctly for the OPs model, then the Dell 9150 BIOS update will do the following and came out on 7/7/06 >>

1. Improve PCIE graphics detection algorithm.
2. Fix memory module detection for SMBIOS.


If his graphics card/onboard graphics are working OK and the installed memory is OK then there's absolutely no need to update unless a new upgraded graphics card or memory will not work.

Advice to OP: if it ain't broke don't fix it.

---

### Post by wpshooter on 2006-12-13
> **BoneKracker said:**
> New machine?  Do you really need to upgrade the BIOS?  

This isn't something to mess with just because there's a newer version available.  Put the wrong version on there and you can end up needing to re-burn the EPROM.  I've seen several people ship their machines back to the factory after diddling around with their BIOS when they didn't even really need to upgrade it.

The USB approach is valid, provided your machine allows you to boot from USB.  Many machines do not.

If not, the simplest fix is probably to borrow the internal floppy drive from another machine, plug it into the motherboard, set the bios to enable booting from it, etc.

There would be NO reason to send your machine back to the manufacturer.  You can send the chip back to them and they will repair or they can send you a replacement chip, usually for a nominal fee.

As far as needing to update BIOS, the manufacturers of these motherboards don't just set around writing BIOS updates for the fun of it.  They are written to fix things that you may or may not even be aware of.  Therefore, generally it is a good idea to keep your BIOS up to the RELEASED but NOT BETA level.

---

### Post by ciscosurfer on 2006-12-13
> **wpshooter said:**
> There would be NO reason to send your machine back to the manufacturer.  You can send the chip back to them and they will repair or they can send you a replacement chip, usually for a nominal fee.

As far as needing to update BIOS, the manufacturers of these motherboards don't just set around writing BIOS updates for the fun of it.  They are written to fix things that you may or may not even be aware of.  Therefore, generally it is a good idea to keep your BIOS up to the RELEASED but NOT BETA level.Agreed. :D

> **ciscosurfer said:**
> People update their BIOS' for a variety of reasons, but mainly to improve its functionality. If I've done my research correctly for the OPs model, then the Dell 9150 BIOS update will do the following and came out on 7/7/06 >>

1. Improve PCIE graphics detection algorithm.
2. Fix memory module detection for SMBIOS.

To the original poster: if you bought this PC after 7/7/06 from Dell, the the newest BIOS will already have been flashed for you. Otherwise you can try to follow their instructions on [this page]("http://tinyurl.com/ygorlv") to copy over the .EXE to a DOS disk (when searching for the correct BIOS update page, I used the following criteria: XPS/Dimension 400/9150). If this is incorrect, please go to the Dell web site and enter the appropriate criteria to get the correct page. If you'd like more detailed instructions, then my [HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=316639") is just a click away. :-)

> **gn2 said:**
> But he hasn't said why he "wants" to update it.

He should only do so if there's a reason why he absolutely "needs" to...

I've done many BIOS updates myself, every time I've done so there's been a compelling reason, and it hasn't always gone well.....



If his graphics card/onboard graphics are working OK and the installed memory is OK then there's absolutely no need to update unless a new upgraded graphics card or memory will not work.

Advice to OP: if it ain't broke don't fix it.In essense I agree with you, however, BIOS updates are generally released to fix important issues, etc.  And that's why I presented the OP with that information so he/she could decide what to do. :D

---

### Post by gn2 on 2006-12-13
> **ciscosurfer said:**
> 
In essense I agree with you, however, BIOS updates are generally released to fix important issues, etc.  And that's why I presented the OP with that information so he/she could decide what to do. :D

I agree that it's entirely up to the OP to decide what to do with his PC, and he should make his own decision and be responsible for it. 

But what if he doesn't have all the required knowledge to safely make the decision?

I take the view that it's better to provide warnings beforehand in all cases where one is warranted.

What if the OP doesn't fully realise the potential harm a failed BIOS flash can cause?

We don't know what he knows, and he doesn't know what he doesn't know, but we can tell him what we know, and if he already knows then no harm done. :)

---

### Post by ciscosurfer on 2006-12-13
> **ciscosurfer said:**
> People update their BIOS' for a variety of reasons, but mainly to improve its functionality.  If I've done my research correctly for the OPs model, then the Dell 9150 BIOS update will do the following and came out on 7/7/06 >>

1. Improve PCIE graphics detection algorithm.
2. Fix memory module detection for SMBIOS.

To the original poster: if you bought this PC after 7/7/06 from Dell, the the newest BIOS will already have been flashed for you.  Otherwise you can try to follow their instructions on [this page]("http://tinyurl.com/ygorlv") to copy over the .EXE to a DOS disk (when searching for the correct BIOS update page, I used the following criteria: XPS/Dimension 400/9150).  If this is incorrect, please go to the Dell web site and enter the appropriate criteria to get the correct page.  If you'd like more detailed instructions, then my [HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789") is just a click away! [:-)]("http://ubuntuforums.org/showthread.php?t=318789")

> **gn2 said:**
> But he hasn't said why he "wants" to update it.

He should only do so if there's a reason why he absolutely "needs" to...

I've done many BIOS updates myself, every time I've done so there's been a compelling reason, and it hasn't always gone well.....



If his graphics card/onboard graphics are working OK and the installed memory is OK then there's absolutely no need to update unless a new upgraded graphics card or memory will not work.

Advice to OP: if it ain't broke don't fix it.

> **gn2 said:**
> I agree that it's entirely up to the OP to decide what to do with his PC, and he should make his own decision and be responsible for it. 

But what if he doesn't have all the required knowledge to safely make the decision?

I take the view that it's better to provide warnings beforehand in all cases where one is warranted.

What if the OP doesn't fully realise the potential harm a failed BIOS flash can cause?

We don't know what he knows, and he doesn't know what he doesn't know, but we can tell him what we know, and if he already knows then no harm done. :)I wholeheartedly concur.  I mention the risks in my [HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789") (also located in my signature) that I've made reference to a few times in this thread.

---

### Post by hardyn on 2006-12-13
He asked a question, how to flash a bios using linux, why can't we just tell him what he needs to do and let that be that?  

I fully respect and expect us, his peers, to provide warning about the possible dangers of a mis-flash; but why do we have to beat the death the philosophy of bios flashing?

give him the info, give him the warning... and if he still chooses to flash and something goes wrong, his problem, sounds simple to me.

---

### Post by ciscosurfer on 2006-12-13
> **hardyn said:**
> He asked a question, how to flash a bios using linux, why can't we just tell him what he needs to do and let that be that?  

I fully respect and expect us, his peers, to provide warning about the possible dangers of a mis-flash; but why do we have to beat the death the philosophy of bios flashing?

give him the info, give him the warning... and if he still chooses to flash and something goes wrong, his problem, sounds simple to me.Because knowing what you're getting yourself into is important and is part of the process.

---

### Post by hardyn on 2006-12-13
> **hardyn said:**
> 
I fully respect and expect us, his peers, to provide warning about the possible dangers of a mis-flash; 


Oh, im not saying not to explain what may go wrong; but we all gotta learn some how, and sometimes learning involves breaking things.  The best lessons i have learned have been the expensive ones.

---

### Post by gn2 on 2006-12-14
> **hardyn said:**
> Oh, im not saying not to explain what may go wrong; but we all gotta learn some how, and sometimes learning involves breaking things.  The best lessons i have learned have been the expensive ones.

Would you let your infant children learn the dangers of fire by allowing them to burn themselves, or would you warn them?

---

### Post by hardyn on 2006-12-14
Again, i don't disagree that he should be warned, but after that, its none of our responsibility what he does with his computer... and children hardly compare with some silicon and fibreglass.

but this forum is here to educate, so... lets educate.


lets run a humorous hypothetical scenario...

"okey so like my best friend's, cousin's, football team mate's, college roomate's ex-girfriend used to work for AMD, and she said if you cut off the keyed pin and install the processor in reverse, you can overclock your system to like 8gh!... im totally going to try it; ill tell you guys how it goes, oh by the way, what is the best tool to cut a pin with?"

i would really hope that after telling me it wont work, and telling me that im an idiot,  i would still be told the best tool to cut a pin.

---

### Post by gn2 on 2006-12-14
> **hardyn said:**
> Again, i don't disagree that he should be warned, but after that, its none of our responsibility what he does with his computer... and children hardly compare with some silicon and fibreglass.

but this forum is here to educate, so... lets educate.


lets run a humorous hypothetical scenario...

"okey so like my best friend's, cousin's, football team mate's, college roomate's ex-girfriend used to work for AMD, and she said if you cut off the keyed pin and install the processor in reverse, you can overclock your system to like 8gh!... im totally going to try it; ill tell you guys how it goes, oh by the way, what is the best tool to cut a pin with?"

i would really hope that after telling me it wont work, and telling me that im an idiot,  i would still be told the best tool to cut a pin.

You don't need to cut it off, just bend it flat ;)

---

