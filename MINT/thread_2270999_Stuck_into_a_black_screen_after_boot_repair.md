---
title: "Stuck into a black screen after boot repair"
date: 2015-03-26
forum: MINT
---

### Post by aka.mdsg on 2015-03-26
Hello

I am posting this from my Android and this forum is the last shot at putting my computer back working again... 

So what happened is.. I had windows 8.1, installed MINT on dual boot but my computer booted directly into windows, I ran the live version through usb once again and used boot repair, it popped up to disable secure boot in the bios but I pressed next anyway because I never had access to the bios in this pc..it happens that now every time I turn the computer on it just gives me a black screen, can't do anything with it... 

I never had access to my Bios,when my computer worked,  it always had gone to Windows with a black screen till it enters the login screen, never seen the boot information in my computer.. I can't access it, neither with my onboard graphics card that is a Intel graphics hd or with my AMD Radeon HD 7750..

I am now without a usable computer, I mean, I have two raspberry pi but that is not very good for daily use as a home computer... 

Need help with this, no clue what I should do.. I tried to reset the bios through the jumpers but it made no difference..

Please ;_;

---

### Post by robsoles on 2015-03-26
Sounds like you really need to access your BIOS settings and disable secure boot.

When you turn the PC on there should be a window of opportunity to enter BIOS by pressing [DEL] or [F2] on most systems.

For better help more information is likely to be required, for starters; What motherboard is your PC using?

(If you cannot answer that question then it is fairly likely that you will have to get the PC in the same room as a 'professional' to get progress with this problem.)

---

### Post by aka.mdsg on 2015-03-26
I am using a Acer DB.SMV11.001 with the prebuilt computer Acer M3985.. 

I know about that sir, I could disable secure boot if I didnt had to do it blindly.. I have no display of the boot, never had, I can't access BIOS and navigate through it if I can't see it ;(

I feel like I have to take this into a repair shop for computers.. I tried so many things including booting into my usb pen drive live Linux Mint but it is kinda hard to do it blindly, no success...

---

### Post by robsoles on 2015-03-26
It is very unusual that your PC does not display POST nor BIOS/CMOS setup. I had a skim of an ACER manual Google suggested to me when I tried 'DB.SMV11.001' in it - the Delete key is the one, if the ratbags I found hosting the manual will let you see from this link: [http://data.manualslib.com/pdf2/45/4453/445226-acer/aspire_x3475.pdf?a57eb142a595aee0b3164aeefa216904](http://data.manualslib.com/pdf2/45/4453/445226-acer/aspire_x3475.pdf?a57eb142a595aee0b3164aeefa216904)

Maybe your monitor is (for some strange reason, never seen by me before) incapable of displaying the particular mode your PC uses for POST and BIOS - please give some details about your monitor and tell whether or not you have an alternative monitor you can try (perhaps a friend with an alternative they will let you try).

Alternatively, maybe if you can try: Power up the PC, wait 1-2 seconds and press Delete key, wait up to about 20 seconds and then press F7 and then press Y (assuming it will challenge 'are you sure?' and "Y" is a valid response - might be 'tab'->'enter', could even require a mouse - very painful) and then press enter (just in case) and then press F10 and try Y and Enter again - if PC reboots at this point you may be about to see the POST and BIOS screens but I wouldn't hold my breath for this to work. Oh, should say; I'm trying to help you load fail-safe defaults in your BIOS, fingers crossed if it doesn't make your display problem go away maybe a fail-safe default will be to have 'secure boot' disabled.


Please don't call me sir, I am just some guy accessing the internet atm (who happens to dislike being called sir...)

---

### Post by aka.mdsg on 2015-03-27
Well, loading defaults for the bios won't do anything because the default has secure boot enabled and I have reseted the bios through the CMOS jumper on the motherboard ... 

I see no solution for this problem, I already tried a.thousand times to boot through the pen drive and it seems I can't do it blindly.. I think it's F12 to choose a different boot option.. I have dual monitors btw, one is vga and one is hdmi but I have been using Vga on both cuz I took my graphics card out to see if I could have display on the onboard graphics card and it only has a vga output so yeah.. no lucky yet.. 

No idea what else to do, I have futsal at 4pm and after I get home I will see if I can take my computer to a repair shop ... 

Thanks for trying to help bro.. unfortunately this case seems to be very difficult to help..

---

### Post by aka.mdsg on 2015-03-27
I managed to do what you told, load the defaults with F10 and then the computer rebooted, it made no difference what so ever, and it is unlikely to be able to disable secure boot blindly xD

---

### Post by robsoles on 2015-03-27
F10 does not load the defaults, F10 saves the current settings.

F7 loads the failsafe defaults, F6 loads the optimum defaults - failsafe defaults may include turning off secure boot.

---

### Post by aka.mdsg on 2015-03-27
I will try the F7 now, il stay with a non working computer for at least two more days so why not give it a try..

will give feedback in some minutes, brb

---

### Post by aka.mdsg on 2015-03-27
didn't help, dunno if my BIOS has failsafe defaults or if it is bound to F7 .. I did F7 - left - Enter .. then F10 - left - enter and it rebooted.. still the same tho |:

tried to do F7 - Tab - Enter .. then F10 - Tab - Enter... also rebooted but did nothing again |:

---

### Post by aka.mdsg on 2015-03-27
I am pretty sure I disabled boot secure blindly with the manual you sent me, however it did not make a difference, my system still doesn't boot into anything and no image on the screen |:

The worse about this is that the repair shop will probably say that is a problem with the motherboard or the hard drive and I will have to pay for it, this only happened after I ran boot-repair in Linux Mint Live Version that is on my usb pendrive .. so it can't be a error with the motherboard/hard drive right? |: I would like to have a new motherboard tho, one that can actually show me the god damn boot up .. that may require a new processor tho, not sure if my i5 2320 is the same socket as a recent motherboard .. I'm screwed xd

---

### Post by robsoles on 2015-03-28
Pity you are unlikely to turn out to be around the corner from me - I'd be perfectly willing to spend at least half an hour with physical access to that thing before apologising one last time and then taking you to a bloke I know running a decent shop who wouldn't try to BS you (especially if he knows I am watching...)

I hope you get somebody in a shop willing to just charge exhorbitantly to fix the truth rather than anyone who will happily lie and replace serviceable stuff - It may be something has failed horribly on the mobo tho, not a great indicator if you never see POST or BIOS messages on it.

---

### Post by aka.mdsg on 2015-03-29
> **robsoles said:**
> Pity you are unlikely to turn out to be around the corner from me - I'd be perfectly willing to spend at least half an hour with physical access to that thing before apologising one last time and then taking you to a bloke I know running a decent shop who wouldn't try to BS you (especially if he knows I am watching...)

I hope you get somebody in a shop willing to just charge exhorbitantly to fix the truth rather than anyone who will happily lie and replace serviceable stuff - It may be something has failed horribly on the mobo tho, not a great indicator if you never see POST or BIOS messages on it.

But if it is a motherboard fail, it fails since I can remember having this pc, I have never seen the boot up in this computer ..

I will try two things before going to a repair shop.. I am using the DVI port with an adapter, one common DVI-D to VGA adapter and then a VGA to VGA cable into the screen, il buy a DVI-D to VGA cable and see if it makes any difference about displaying the boot, but I am not expecting this to work... 

Wednesday I will take my hard drive to a friends' place, put it into his computer and format it with windows 8.1, then il put it back into my computer and see if it boots correctly .. this one may work, dunno.. if both of my options fail, then I will take it to a repair shop, and most likely pay for something ... I won't mind paying for a new motherboard tho, with a recent BIOS and one that actually shows me the boot .. xD

And I am from Portugal so most likely I am not around the corner from you but thanks anyway :)

---

