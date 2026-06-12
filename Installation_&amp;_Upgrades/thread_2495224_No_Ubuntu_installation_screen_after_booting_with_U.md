---
title: "No Ubuntu installation screen after booting with USB ISO image"
date: 2024-02-12
forum: Installation &amp; Upgrades
---

### Post by orb8873 on 2024-02-12
Hello, newbie here.
After formatting a USB stick using my Windows PC, I used Balena Etcher to make this USB stick bootable from this download:  Ubuntu-22.04.3-desktop-amd64.  Balena Etcher indicated that the flashing completed successfully.  With this USB stick inserted into my PC, I tried to boot to the BIOS screen and selected this USB drive to boot from, however I then only got a black terminal screen with a grub> prompt, after error messages were displayed for about 100 milliseconds (too fast to read) instead of the Ubuntu installation screen that I expected to see.  I tried this with two separate USB sticks (64GB and 256 GB) with the same result.

Could someone please advise me what I’m doing wrong?

Thank you.

---

### Post by Rubi1200 on 2024-02-12
Hi and welcome to the forums :-)

What are your system specifications, especially graphics card?

I would download and use Rufus from Windows. Choose to write to the USB in dd mode, not the recommended ISO mode.

Also check in BIOS if you have fast startup, hibernation or secure boot enabled. Disable those first before trying to boot the liveUSB.

Let's see if any of this gets you further before suggesting other options.

---

### Post by orb8873 on 2024-02-12
Thank you for the information.  Before rewriting the Ubuntu image to my USB drive using Rufus, I want to reformat it to remove the previously attempted ISO image.  However Windows will not start the format process because it returns the message:  "disk is write protected", perhaps because it does not recognize the Balena Etcher ISO image.  I used the Microsoft Disk Part utility library to remove the read only attribute, but Windows format still does not work.  I would prefer not to have to purchase a new USB stick if I can simply reformat my existing one.  What should I try next?  I will address your other questions after I'm able to successfully rewrite the Ubuntu image to the USB stick.

---

### Post by Rubi1200 on 2024-02-13
I would do it like this:

1. Open Rufus
2. Drag and drop the ISO image to the Boot selection for ISO
3. Put the USB in and let Rufus detect it
4. Select to write in dd mode
5. Double check you are about to write to the correct USB stick

Start the process. Rufus will warn about overwriting data etc. but that is what you want.

In theory, the steps above should work without any need to format the USB beforehand.

---

### Post by orb8873 on 2024-02-17
Hello again,
I completed the Ubuntu installation on my PC per your instructions.  It boots fine, just curious about the "Error Communicating to TPM Chip" message that appears in the black terminal screen prior to Ubuntu start up, should I be concerned?.  Any recommendations for good antivirus software for Ubuntu?

Thank you again for your help!

---

### Post by Rubi1200 on 2024-02-17
I have not seen that error message before and would not like to comment on its meaning. If the system boots fine and you can get to the desktop, then likely nothing to be concerned about.

You do not need antivirus on Linux unless you are perhaps sharing files with Windows users.

See more here for a general overview of Ubuntu security:
[https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

---

### Post by yancek on 2024-02-18
TPM is trusted platform module and you should find something referencing it in your BIOS.  It may not be specifically TPM so do an online search mentioning your specific hardware.  On my HP laptop, it is under the Security tab.  I am able to boot all my Linux systems with TPM enabled or disabled but windows won't boot if it is disabled.  Should not be a problem for you with Ubuntu.  Some discussion of the message at the link below.

[https://askubuntu.com/questions/1178285/how-to-solve-ima-error-communicating-to-tpm-chip-messages-during-boot](https://askubuntu.com/questions/1178285/how-to-solve-ima-error-communicating-to-tpm-chip-messages-during-boot)

---

### Post by yancek on 2024-02-18
A computer virus is simply an executable file that does something the user did not want or intend to do.  An executable windows file won't do anything on Linux.  There is some fairly reputable antivirus software for Linux, I've never used any and have never had a 'virus' on any computer.  More likely to get malware of some kind but even that won't work the way it is intended because it was designed to run on windows.  The link below discusses particular malware like this which can appear in a browser on Linux.

[https://answers.microsoft.com/en-us/windows/forum/all/how-do-i-get-rid-of-the-windows-defender-security/5475db1b-6d31-4406-8c1c-7799ba22165d](https://answers.microsoft.com/en-us/windows/forum/all/how-do-i-get-rid-of-the-windows-defender-security/5475db1b-6d31-4406-8c1c-7799ba22165d)

---

