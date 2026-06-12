---
title: "Absolutely fed up!"
date: 2006-04-22
forum: Installation &amp; Upgrades
---

### Post by matelot on 2006-04-22
I consider myself new to Linux after a disastrous and unsuccessful experience with Mandrake years ago... ](*,)

I've downloaded the ISO (Live CD) for 5.10 on three separate occasions from three different sources. None of this was easy because I had about 15 ISOs to choose from and a list of about a thousand checksums. [rant mode on]So far no-one has been able to point me to a site which is simply and intuitively laid out with explanations and instructions... now do this, now click here. It's all geek-speak.[/rant mode off]

Anyway, I've used two different burning methods on three CDs (one a CD-RW) as recommended on Linux forums. The CD runs in a Windows environment for the tour of ubuntu: no probs. All the CDs boot OK, but then the install stops at exactly the same place after language and keyboard selection saying it can't read from the CD. I then run the CD check option. Guess what? CD OK! I know the CD is OK, so is there a conflict somewhere?

To get out of the interminably recycling screen, I have to pull the plug. There's no option to abort the installation after a certain point. :???: 

If the Linux community would like more people to use Linux, why is it so difficult. HELP!! ](*,) ](*,) ](*,) 

Dell 3000 512Mb RAM, 160Gb HDD, Win XP Home. Usual stuff and one year old.

---

### Post by aysiu on 2006-04-22
[QUOTE=matelot]
If the Linux community would like more people to use Linux, why is it so difficult. HELP!! ](*,) ](*,) ](*,)[/QUOTE] Learning to do a checksum and burn an .ISO at low speeds isn't a Linux thing. If you want to avoid this, buy a CD set of Linux (Ubuntu doesn't do this--as it sends its CDs free... well, after about two months--but other distros do sell boxed sets, just as Windows does).

---

### Post by matelot on 2006-04-22
Thanks, but are you saying that it's just the burns that are at fault? I downloaded one with BitTorrent which claims to validate the checksums, and I also validated one independently. But all three stop at EXACTLY the same point in the install. That's not really faulty downloading or burning, is it? :???:

---

### Post by aysiu on 2006-04-22
Hm.

Well, when the install fails in the middle of the installation, it usually means one of three things:

1. Bad .ISO image (corrupted during download)

2. Bad CD burn (corrupted during burn)

3. Faulty hardware (CD-ROM drive or other hardware not working properly)

Maybe it's a bad CD burn. Did you burn at a slow speed--something like 4x? Higher speeds (like 48x) sometimes corrupt even a perfectly good .ISO.

---

### Post by matelot on 2006-04-22
1. Could be corrupted (three times?) but checksums validated and BitTorrent claims to do it anyway;

2. Could be, but I set it to burn at 12x as advised on a link from ubuntu's homepage;

3. Don't think so... From Windows, everything is tickety-boo. No conflicts. Everything runs smoothly. But halfway through an install which baulks, how do I check? I have to pull the plug.

May try the CDs if it's so insanely complicated to download and install... :-?

---

### Post by aysiu on 2006-04-22
It sounds as if you're doing everything right, and if you tell me the hardware's good, it's probably good. I don't know what else it could be.

I know that #1-3 are the only reasons I've seen for an install failing part-way through. Who knows? Maybe there's some other possible explanation I just don't know.

---

### Post by henriquemaia on 2006-04-22
[QUOTE=matelot]
2. Could be, but I set it to burn at 12x as advised on a link from ubuntu's homepage;[/QUOTE]

I had an issue similar to yours with one of my installs. I corrected it by burning the CD at the **recorder's lowest speed **(4x in my case). I had previously tried to burn it severall times but it always hung somewhere during the installation process.

Low speed burning was the answer.

---

### Post by matelot on 2006-04-22
Then I'll try that on a CD-RW. Won't waste the CDs then!

Cheers. I'll let you know the outcome, but if there's any more input from you peeps, I'm still open to (polite :mrgreen: ) suggestions. 8)

---

### Post by matelot on 2006-04-22
Pants. I verified the checksum of the ISO, and burned it at only 2x. It stopped again in exactly the same place. After selecting language, keyboard etc., it comes up with: *Can't read from CD - can't load installer components*. This was another new CD-RW.

I give up! ](*,) 

What else can I do?

---

### Post by Buffalo Soldier on 2006-04-22
Short version: Malfunctioning CD-burner.

Long version: Something like this happened to me once. It was around when Dapper Flight 3 was released. I was burning ISO to CD using a desktop PC at home (usually my father and brother use this PC). I probably used 4-6 CDs, burned at various speed and using ISO downloaded using torrent. None  were usable.. stucked right in the middle of installation (can't remember the exact moment).

Then using the same ISO (copied thru homenetworking/samba) I burned it using my laptop burner and everything works fine. I found out the long and hard way that my desktop PC burner is kaput.

---

### Post by henriquemaia on 2006-04-22
[QUOTE=matelot]Then I'll try that on a CD-RW. [...][/QUOTE]

I always use CD-RW for distros. That's a good idea.


[QUOTE=Buffalo Soldier]Short version: Malfunctioning CD-burner[/quote]

You're right. 

Verify your hardware burning on another CD recorder if you can, matelot.

---

### Post by matelot on 2006-04-22
Always a sucker for punishment!:mrgreen:  I'll give it another go...

Cheers

PS - the ISO for DamnedsmallLinux burned fine and it runs OK from the CD, so...

---

### Post by az on 2006-04-22
You may need to boot with some special options if you have certain hardware. Look at the help screen.  Also, Change console to the error screen (CTRL-ALT-F3) if you can and post the error where you get stuck.

---

