---
title: "Help against hackers"
date: 2015-08-20
forum: MINT
---

### Post by marc43 on 2015-08-20
I have this co-worker who likes to boast that his mates all use Kali Linux. Right after this, a very important file on my laptop was compromised. (This isn't the first time, but the most recent.)

The attack baffled me, because I took all the security precautions I'm aware of. For example, the file that was "hacked" was redundantly backed up as follows:

1 copy in my Documents folder.
1 copy on external HDD partition 1
1 copy on external HDD partition 2
1 copy on usb thumbdrive
1 copy on Google Drive

The ods file was protected with a 16 character alpha-numeric-symbol password, yet all five copies gave me a nebulous "read error". Even after I wiped and reinstalled my OS and bought a new computer and tried it on that.

UFW is active. Default is deny all incoming. (I now have a second firewall as I bought a bridging router.)

Apache2 is not install and neither is mySQL. Finally, I even use a VPN for surfing.

Can someone tell me how I might have been hacked, and what further steps I can take to make this OS as rock hard as possible?

OS: Linux Mint 17.2 (based on Ubuntu)

Much appreciated.

---

### Post by PaulW2U on 2015-08-20
*Thread moved to **MINT*** as you're not using an official Ubuntu flavour.

---

### Post by marc43 on 2015-08-20
Thanks.

---

### Post by blitz2 on 2015-08-20
hmmm suspicious :-k Did you look up to log files if there was a suspicious activity? I recommend you to use it. Actually i'm using Ubuntu but it must be the same. 

Type to console for authentication attempt and look it up;

less /var/log/auth.log (history of authentication)
or
cat /var/log/auth.log

For UFW;
less /var/log/ufw.log
cat /var/log/ufw.log
Now you are telling reinstalled your OS! It's really hard to say if you are hacked or not

---

### Post by marc43 on 2015-08-21
Yeah. I reinstalled the OS and eventually migrated to a new computer for a couple of reasons.

It is suspicious, because the copy of the file on Google drive was about 1.5 weeks old, so even if all four local copies became infected with a macro (which I never use) or something, the one on Google Drive should have been ok. All employees use a company network at home, and I'm guessing that they used something like wireshark and just waited until my VPN was down or something. (Even so, I don't know how they could isolate my internal IP unless they were watching traffic network wide and just waited until something that linked me with a specific IP turned up.)

 Since then, I've bought a private router with a built-in firewall to bridge between my computer and that network.

But this isn't the first time this has happened since I became employed at this company. I had a much greater loss back in June when many files suddenly became inaccessible. Fortunately, I had made a hard copy of a 300 page document before this happened and I'm still in the process of OCR scanning it back in.

I realize the damage is done, but I also realize there are some major holes in my understanding of security, and that's what I'm really asking for help with. Thank you though. If this happens again I'll know which log files to look at before wiping out the hard-drive.

---

### Post by montag dp on 2015-08-21
Are you positive that the original file was not corrupted before you made copies of it?  Because to me, that sounds like the most logical explanation.

---

### Post by marc43 on 2015-08-21
I would absolutely agree with you, except that the file uploaded to Google Drive was in perfect working order and uploaded about 1.5 weeks prior to having any problems with the local files. I upload manually, so there is no possibility of unintentional over-writing. (My computer doesn't auto-sync with Google Drive.)

This has happened numerous times over the last two years. I don't want to get into details, but I think I pissed someone off. However, I don't have any information that could damage anyone. This is simple a case of having the nasties on my ass...

...and I want to stop them.

OK. I spent a lot of time yesterday with Harden and some other stuff. Hopefully that will help. This same file has been hit 3 times this year, and I've had to buy 5 laptops in the last 2 years. Anyone willing to discussing this without judgement about motives is most welcome.

The help would be very welcome.

Fine. May the weight of the future rest upon your heads then.

---

### Post by MartyBuntu on 2015-08-22
Keylogger, perhaps?

---

### Post by CharlesA on 2015-08-23
> **MartyBuntu said:**
> Keylogger, perhaps?

Perhaps, but that would more than likely require physical access to their machine and shouldn't survive a reinstall.

With that said, are any of these copies of whatever file is inaccessible versioned or are they are direct copies?

Versioned backups are necessary for good computer security.

---

### Post by trtle on 2015-09-09
wouldn't you get a read 'error' if you forgot the password, or your key was compromised?  Maybe use a symmetric cipher to encode it so the password is easier to remember.

---

