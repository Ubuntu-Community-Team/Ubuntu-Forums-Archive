---
title: "&quot;acpi int3400 unsupported event&quot; - Killing A New Awesome Laptop"
date: 2018-09-12
forum: Installation &amp; Upgrades
---

### Post by markackerman8@gmail.com on 2018-09-12
I just received a Omen x 17-ap0xx potentially awesome laptop

And While installing on the new blazing fast NVMe PCIe M.2 drives, I see over 50-100
yes 50-100 

"acpi int3400 unsupported event" ERRORS while the install is going on

and yes I have installed over 20 times since last night - trying both the NVMe 1 TB drive and the 512 PCIe Sata previously perfectly functional drive my previous Omen from 2 years ago now returned 

I have got to a shaky login screen and I mean shaky, and when (if it does log in and it gets way better, until the next reboot), and the thing that invariably kills the next reboot is installing any of the NVidia drivers.

Then the error on shutdown and start gives thousands of "acpi int3400 unsupported event" endlessly - ENDLESSLY, and won't even get to the login screen.

Please I would hate to be stuck in Windows AFTER helping hundreds over the past 10 years, just when I thought Ubuntu was getting great

Please Please help troubleshoot - I am at a complete loss. 

I will try anything

---

### Post by markackerman8@gmail.com on 2018-09-12
I am desperately going to try another install after taking out my newly installed 1 TB NVMe - to see if it helps.  At least I will keep a basically disfunctional Ubuntu open for troubleshooting

Thanks in advance

---

### Post by QIII on 2018-09-12
Hello!

Take a deep breath!  :)

I have 3 NVMe devices in my daily driver (no 2.5'' SSDs or mechanical drives, all NVMe) and things are fine.  So this so likely solvable and may take little effort.

While you are experimenting with moving the drives, could you post the full specs of your machine?

Thanks.

Edit:  Does [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1786906") look like it may apply to your situation?  I'm wondering if it is hardware-specific.

---

### Post by markackerman8@gmail.com on 2018-09-12
Hp Omen X 17-anoxx
&#8227; Intel® Core&#8482; i7-7820HK CPU @ 2.90GHz × 8 
&#8227; GeForce GTX 1080M
&#8227; 16 GB RAM
&#8227; 1 TB NVMe PCIe M.2 3 GB/s Read 1.5 GB/s Write (brand new and replace the 256 Gb NVMe it came with - similar but SMALLER )
&#8227; 512 Sata PCIe M.2 2 years old (Was working flawlessly on an older Omen and i was able to save it)
&#8227; 1 TB 7200 Sata HDD

---

### Post by markackerman8@gmail.com on 2018-09-12
and so far so good (the 26th hour NON STOP - no sleep - obsessed with getting this working after waiting for 3 1/2 weeks for my Hp replacement ! Arghh!)

and Taking a deep breath Thanks You! Q111

---

### Post by QIII on 2018-09-12
So you've removed the 1TB NVMe device and the machine is behaving?

---

### Post by markackerman8@gmail.com on 2018-09-12
and for the record the top post 38 minutes ago was from Windows WORKING FLAWLESSLY on the said machine.

I have restarted successfully after logging out of windows - SURPRISINGLY - I thought it was hosed again!  So no new install as of yet
5 restarts as I am slowly installing Things (but way too afraid to install the Awesome Nvidia Driver - which has been awesome till the nexr resart - and ALWAYS hosed!
here are the number of identical aforementioned errors
200
(Router Restart - Trying Anything)
25
50 
75
250+

---

### Post by markackerman8@gmail.com on 2018-09-12
No I WAS going to remove and will next when this install goes SOUTH - for now it is hanging on

---

### Post by QIII on 2018-09-12
Does Ubuntu work with the original NVMe device?

What I'm getting at here is that you may indeed be a victim of the bug I referenced.

---

### Post by QIII on 2018-09-12
Ah.  I see post #8 now.

Fingers crossed.

---

### Post by markackerman8@gmail.com on 2018-09-12
> **QIII said:**
> Does Ubuntu work with the original NVMe device?

What I'm getting at here is that you may indeed be a victim of the bug I referenced.

The Root and ?home and Swap is now all on the origional, and was my last attempt before my first post.  ANd it wojuld Not restart untill a went into Windows to make the first post and tried to resart into Ubuntu for giggles and grins, and thats is where the last remaing posts have been

---

### Post by markackerman8@gmail.com on 2018-09-12
Still averaging 100 errs+ on each 5 restarts since

---

### Post by QIII on 2018-09-12
OK.

Unfortunately I think you are in the bug boat.  My guess is that some hardware specific code is at fault.

Create a LaunchPad account and have a look at that bug.  Click "Affects me" to fan the flame and detail what you've done.  It looks like the original reporter did not include all the expected logs, so you might want to so that triage can begin at Canonical.

Ubuntu can wait for now.  Don't continue to bash your head!  It's just not worth it!

---

### Post by markackerman8@gmail.com on 2018-09-12
And what Has ALWAYS put it to the point of ENDLESS Errors and No Login Screen and/or won't shut down ....

 is the Nvidia Driver Install which I am dreading and can't reasonably live without

---

### Post by markackerman8@gmail.com on 2018-09-12
snif snif

---

### Post by markackerman8@gmail.com on 2018-09-12
Any TroubleShooting Tips

Some good ole Command line requests that might pin down whats happening - I am not very good with them at all

---

### Post by QIII on 2018-09-12
Frustrating!  I would be frustrated, for sure.  You spent some good money on that machine from the looks of it.

---

### Post by markackerman8@gmail.com on 2018-09-12
Yep My last Laptop of my life perhaps $3,400 in a desperate attempt to use my $350 1 TB NVMe I ordered from Canada Computers for my Rich Twins Asus ROG and onbe for me/me - so that's $4,000 Canadian, and I thought it would be awesome - 13 years struggling with Linux helping all I could help -

 oops just rambling sorry

---

### Post by markackerman8@gmail.com on 2018-09-12
and a successful restart again 
5 seconds to Shutdown, and 10 seconds to Login Screen
Only 30 errors

before shutting down I went into disks and clicked on repair each disk and drives (10 or so) twice that I could - perhaps making a difference - Wishful thinking I think

---

### Post by markackerman8@gmail.com on 2018-09-12
ok just install Synaptic and all the "Indexing Files which scared me a tad scared over 2 minutes to shutdown - repeating Cntrl/Alt/Delete ... but 10 seconds to restart and only 10 I thought but re-looked and nope 150 damn errors

---

### Post by markackerman8@gmail.com on 2018-09-12
OK SO I am ready to try and install the friggin awesome gtx-1080m Nvidia driver -  which has killed 10 installs (Debian and Ubuntu a like in the last 28 hours)

So here I go again 

Any last advice on how to do this perhaps somehow more controlled or safer, and yes I will install the 396 driver from the ppa

5 minutes to countdown

and yes just uninstalling and/ purging WIll Likely Not Bring back the present semi functionality - i.e. has killed it irreparably  over 7 times - arghhhh!

---

### Post by markackerman8@gmail.com on 2018-09-12
Installing Wish me Luck - I will post either way after installing the 396 open source nvidia driver for a 5th time and restarting

just 20 errors last 15 second reboot WooHoo!

---

### Post by QIII on 2018-09-12
Can you use Clonezilla or dd to capture the state of your OS first?  Might save some frustration if everything goes sideways.

---

### Post by markackerman8@gmail.com on 2018-09-16
For anyone reading this - the error is 90% solved making my Ubuntu restarts usable but TTY3 to console still gets it.

The solution was very easy ...

Hp does not play with a clean ACPI set of rules that Ubuntu expects - to sum it up. So restricting it or turning it off has worked for many.  In my case restricting it worked absolutely best.

add to grub's line... 
[PHP]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"...[/PHP]
```
sudo gedit /etc/default/grub
```

&#8227; "acpi=off" or "noacpi" "acpi=strict"

&#8227; "acpi=strict" WORKING BEST as of 09/15/18
so the line looks like this:

[PHP]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=strict"...[/PHP]

I hope it helps others

Mark fewwwww:p

---

### Post by thinkpadt480 on 2019-04-10
[3477.809666] acpi INT3400:00: Unsupported event [0x88]
[40906.397045] acpi INT3400:00: Unsupported event [0x88]

How to solve this?

---

