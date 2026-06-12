---
title: "Can't LiveCd with Dell because no visible BIOS"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by newmo on 2007-01-17
I am trying to introduce a friend to the joys of Ubuntu.  I have put together a very basic "first lesson" about how to set up a machine so that it will boot from a CD.

He says there is no BIOS - the machine boots into XP fine but there simply isn't the text appearing before starting up Windows so he can't do the pause| break button thing and so on.  It's so frustrating as he's been expressing quite a bit of interest and he can't even try out a few live distros.

I said I'd look around for answers for him but have had trouble finding solutions.

He emailed me this 

> So I did some research and I found a message board where ppl said that what you do is power off, disconnect everything, open 'er up and remove the little round battery which sits on the motherboard. It then goes back to the factory default settings.
 
So I did this and went out.
 
I came back around two ours later, put it all back together. The comp now thought it was August 2004 which is strange as I'm sure I bought it in 03. Still no BIOS though.
 
Next stage: I mess about with System Configuration Utility. Fun! 

Has anyone heard of such a thing before?  Is there some kind of non-verbose mode with Dell machines which hides the text but is purely cosmetic with the BIOS actually running in the background?  Any other diagnosis?

I am not able to access his machine but if anyone can offer suggestions I'll point him here.  All I know about the hardware is its a Desktop Dell about 4 yrs old costing slightly over the £500 at the time and that he's put it through an upgrade or two and he's certainly reinstalled XP a couple of times on it if that helps.

Thanks

---

### Post by taurus on 2007-01-17
When the machine first boots up, press F2.  What model Dell is it anyway because we have a bunch of Dells (old and new) here at work?

---

### Post by dcstar on 2007-01-17
> **taurus said:**
> When the machine first boots up, press F2.  What model Dell is it anyway because we have a bunch of Dells (old and new) here at work?

If I remember correctly F12 on a Dell will bring up the Boot Options screen (if it is not disabled).

---

### Post by kebes on 2007-01-17
Some computers will hide the message that says "press F2 to enter setup" but it's still there... when the computer first boots up (there may be a DELL logo on the screen for an instant), you just have to press the right key. Look up the exact model number of the computer (or motherboard, if you can find out what it is) and somewhere you'll find what the "magic key" you need to press is!

See this page:
[http://www.michaelstevenstech.com/bios_manufacturer.htm](http://www.michaelstevenstech.com/bios_manufacturer.htm)

Scroll down to the "Dell" section... it lists the BIOS key for a variety of models.


Hope that helps.

---

### Post by newmo on 2007-01-18
Thanks everyone

I will refer my friend here and if needs be he can post more details... *I think* he has tried one of the F keys that turned up as solution elsewhere but without luck.  It might just be the wrong one for his model.

Thanks again

---

### Post by taurus on 2007-01-18
Just look at the front of the case to see what model it is.  We have Dells going back to P3 450MHz (got 30 new ones a couple of weeks ago) so we have all kind of models running around here.

---

### Post by amun on 2007-01-18
I'm the guy who can't get into his BIOS.

The pc's a Dimension 4600.  

The motherboard details would appear to be

Board: Dell Computer Corp. 02Y832 
Serial Number: ..CN4811135907XH.
Bus Clock: 533 megahertz
BIOS: Dell Computer Corporation A12 08/26/2004
(from Bellarc Advisor).

In case it's not clear what happens when I switch on the pc is I go from a blank screen to the cursor appearing then into windows. The Dell logo does not appear.

I've tried jabbing repeatedly at F2, F12 & delete when I switch on. The screen remains stubbornly blank but does not go to windows.

I'd be grateful for any suggestions.

Thanks

---

### Post by _simon_ on 2007-01-18
Reading round it definitely appears that you either need to be pressing F2 **or** DEL.

As to why it's not working, I'm guessing you're not pressing it soon enough.

I suggest that from the moment you press the power button that you start pressing F2 repeatedly, if that fails then do the same again but with DEL. If that also fails then I dunno!

---

### Post by taurus on 2007-01-18
Does it come with a user manual that you can look up to see what key (or combination of keys) you have to press to get into the BIOS?

---

### Post by amun on 2007-01-18
> **dcstar said:**
> If I remember correctly F12 on a Dell will bring up the Boot Options screen (if it is not disabled).

I think that maybe it is disabled. Off to the Dell forums.

Thanks

---

### Post by bigken on 2007-01-18
its F2 could be a bad key :-k

---

### Post by amun on 2007-01-18
> **taurus said:**
> Does it come with a user manual that you can look up to see what key (or combination of keys) you have to press to get into the BIOS?

Yes, and I've looked at it in the last few days (but can't see where I left it now) and it said F12. Pressing F12 does produce a beep from the motherboard speaker whereas pressing 
F2 or delete doesn't.

Thanks

---

### Post by _simon_ on 2007-01-18
Manual for Dimension 4600:

[http://support.dell.com/support/edocs/systems/dim4600/en/4600/sm/sysset.htm#1106146](http://support.dell.com/support/edocs/systems/dim4600/en/4600/sm/sysset.htm#1106146)

Says you should get a dell logo, that's when you press F2 but you said you don't get one... ?

F2 = Setup
F12 = Boot Menu

Pressing F12 SHOULD give you a list of bootable devices in a small menu in the top right of your screen.

---

### Post by taurus on 2007-01-18
> **_simon_ said:**
> 
Says you should get a dell logo, that's when you press F2 but you said you don't get one... ?

F2 = Setup
F12 = Boot Menu

Pressing F12 SHOULD give you a list of bootable devices in a small menu in the top right of your screen.

That's what I have on my Dell Optiplex 620 too.

Big Dell logo in the middle of the screen and in the upper right corner, there are those two options...

---

### Post by _simon_ on 2007-01-18
I don't know what country you are in but Dell do online technical support in real time.

Here's the euro link [Clicky](http://support.euro.dell.com/support/topics/topic.aspx/emea/shared/support/chat/en/hardware_chat?c=uk&cs=ukdhs1&l=en&s=dhs)

US link [Clicky](http://support.dell.com/support/topics/global.aspx/support/chat/en/hardware_chat?c=us&cs=19&l=en&s=dhs)

---

### Post by amun on 2007-01-18
> **_simon_ said:**
> I don't know what country you are in but Dell do online technical support in real time.

Here's the euro link [Clicky](http://support.euro.dell.com/support/topics/topic.aspx/emea/shared/support/chat/en/hardware_chat?c=uk&cs=ukdhs1&l=en&s=dhs)

US link [Clicky](http://support.dell.com/support/topics/global.aspx/support/chat/en/hardware_chat?c=us&cs=19&l=en&s=dhs)

I'm in the UK but I'm way past my warrantee period so Dell won't want to know. 

Thanks anyway.

---

### Post by amun on 2007-01-18
> **taurus said:**
> That's what I have on my Dell Optiplex 620 too.

Big Dell logo in the middle of the screen and in the upper right corner, there are those two options...


Used to get the big Dell logo but I don't get it anymore. I've reinstalled windows twice on this machine but no way can I do it now. I get blank screen/cursor/windows. That's it.

Thanks for your input.

---

### Post by amun on 2007-01-18
> **_simon_ said:**
> Manual for Dimension 4600:

[http://support.dell.com/support/edocs/systems/dim4600/en/4600/sm/sysset.htm#1106146](http://support.dell.com/support/edocs/systems/dim4600/en/4600/sm/sysset.htm#1106146)

Says you should get a dell logo, that's when you press F2 but you said you don't get one... ?

F2 = Setup
F12 = Boot Menu

Pressing F12 SHOULD give you a list of bootable devices in a small menu in the top right of your screen.

Yes, the whole prob is I don't get what I should when I turn the PC on. Starting to think I may need a new pc as I cannot see a way round this. 

Thanks

---

### Post by Quantux on 2007-01-18
So if you start hitting F2 as soon as you turn the power on, you get nothing? This works on all the Dell's I have access to. Don't hold it down, you'll get a kbd error.

---

### Post by _simon_ on 2007-01-19
> **Quantux said:**
> So if you start hitting F2 as soon as you turn the power on, you get nothing? This works on all the Dell's I have access to. Don't hold it down, you'll get a kbd error.

He actually needs F12 for the boot menu but neither work.

Maybe if the BIOS was re-installed or the latest one installed (if you don't already have it) it might put things right.

---

### Post by amun on 2007-01-19
> **_simon_ said:**
> He actually needs F12 for the boot menu but neither work.

Maybe if the BIOS was re-installed or the latest one installed (if you don't already have it) it might put things right.


I downloaded the latest update (August 2004) a coupla weeks ago. No joy.

Reinstalling BIOS...hmmm. I'll look into it.

Thank you all for your help.

---

### Post by bigken on 2007-01-19
dont want to sound rude but you dont install bios you flash it 
and if your bios was corrupt or faulty the pc would not boot at all 


just a thought is your keyboard usb 

is usb support enabled in the bios for legacy

if it is usb try a ps2 keyboard

---

### Post by bigken on 2007-01-19
oops forgot its a laptop :lolflag:

---

