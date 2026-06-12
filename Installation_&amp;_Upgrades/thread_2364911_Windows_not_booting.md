---
title: "Windows not booting?"
date: 2017-06-29
forum: Installation &amp; Upgrades
---

### Post by wmarkley76 on 2017-06-29
Hi everyone,

I'm new to Ubuntu, and I'm trying to install it on my Acer computer, currently running Windows 8.1. I've created a bootable USB stick, and I have restarted my computer with the stick inserted. However, when I get to the screen which asks me which OS I want to continue with, and I choose Linux, I get this message:
[IMG]https://mail.google.com/mail/u/1/?ui=2&ik=a6244f6ac8&view=fimg&th=15cf491451059400&attid=0.1&disp=inline&safe=1&attbid=ANGjdJ8_ykcskqxbSVxSyY5dr5o4jLMPVFkyXLO2OQmk2TnFJBi-Gp00xt56Fjo3PUCLNW38Im5v34cBYlCkzu1cClsyX_lLkNVHuCiNUD92fnw--kncJmYc7H7GUB8&ats=1498751843817&rm=15cf491451059400&zw&sz=w1366-h633[/IMG]

Any solutions? Thanks in advance.

---

### Post by Autodave on 2017-06-29
What is the message? (Can't see it in your post.)

Are you trying to dual boot and keep Win 8.1 and have Ubuntu on it, too?  Or, are you trying to just run Ubuntu from the USB stick?

What are the specs of your machine?

---

### Post by wmarkley76 on 2017-06-29
Sorry for the lack of information. The picture reads: 

Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert your Windows installation disc and restart your computer
2. Choose your language setting and press Next
3. Click "Repair your computer"

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

File: /g21dr.mbr
Status: 0xc000007b

Info: The application or operating system couldn't be loaded because a required file is missing or contains errors.

I'm just trying to run Ubuntu from the USB, although I would like to know if this is the right choice rather than dual booting

I have an 64 bit Intel Celeron N2820 processor with a speed of 2.13 GHZ.

---

### Post by yancek on 2017-06-29
Windows 8 and 10 use UEFI by default if pre-installed.  Is that the case or did you install 8.1 yourself possibly using the older MBR method?  If I understand your post, you are still at the point where you are trying to boot the Ubuntu media to install, is that correct?  If so, you need to access the BIOS/Setup immediately on boot and change the boot priority to the usb.  I'm not sure where you are seeing the choice for 'Linux' on boot if you haven't installed??  I'm not familiar with the Acer BIOS but you should see some option in BIOS Setup to boot from usb

Also clarify what your intentions are.  You indicate you want to run Ubuntu from usb but not whether you want to do an actual full install to the usb or if you want to just boot the usb as a Live Media.  You can do either but for the second option, you will not keep any changes on reboot.

---

### Post by wmarkley76 on 2017-06-29
Immediately after rebooting with the USB inserted, I get this prompt:

[IMG]https://mail.google.com/mail/u/1/?ui=2&ik=a6244f6ac8&view=fimg&th=15cf65e86b3c3ac4&attid=0.1&disp=inline&safe=1&attbid=ANGjdJ8N5KOH76mEc5vbBEMCDJun6jVgSf8vNnPQuMXcYMg8G8jodklI6G3CCKLkbNq1mflqPv04u3c0Cc7uq-9WVEWAuryhV7Lu44A_6fsYc1DmlL6kk6nE2YfBwBM&ats=1498782234507&rm=15cf65e86b3c3ac4&zw&sz=w1366-h633[/IMG]

After selecting Linux, I get the error message seen above. I'm not sure how to change the boot settings, as the F12 key does not pull up the boot menu for me when I'm restarting my computer. As for what I intend to do, I plan to follow the tutorial on the Ubuntu site for Ubuntu for desktop. Sorry for my lack of expertise

---

### Post by yancek on 2017-06-30
Different manufacturers have very different settings so you will probably need to do an online search, something like Acer UEFI BIOS settings.  If you have the specific model information for the computer you could do an online search for it's manual.  Those are usually posted at the manufacturer site.

On boot you should also see an option to access the BIOS/Setup by hitting a certain key.  You need to keep a close watch as it is not there very long.  On the HP laptop I just got, it's on-screen for less than 2 seconds.  

The error message you posted seems to indicate that some change was made.  I'm not sure what or how if you are just trying to boot the USB and haven't got to the point of trying to install?

---

### Post by Mark Phelps on 2017-07-02
Unless it is your intent to entirely replace Win8x with Linux, then DO NOT use the Linux installer to shrink the Windows partition to make room.  Doing so often causes file system corruption and since Windows will then NOT boot anymore, that will be very hard to fix.

Instead, boot into Windows and use Disk Management to shrink the Windows OS partition to leave some room.

Then, use the Something Else option in the Linux installer to format the empty space.

---

