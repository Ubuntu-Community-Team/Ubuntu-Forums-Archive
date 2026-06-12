---
title: "&quot;Try Kubuntu&quot; 15.04 crashes on 2 PC's with 14.10"
date: 2015-04-26
forum: Installation &amp; Upgrades
---

### Post by hjvdmolen on 2015-04-26
This weekend downloaded, burned & verified the Kubuntu 15.04 image.
However, when booting from this dvd and selecting "Try Kubuntu" both my desktop PC's with Kubuntu 14.10 halted.
[LIST]
[*]The newest PC with a P8Q67-M DO/TPM motherboard crashed with a blank screen.
[*]The oldest PC with a WMCP61M motherboard crashed with a distorted screen.
[/LIST]

Both PC's have been running various Kubuntu versions for years and were able to boot into Linux Mint 17.1 Cinnamon 64-bit (Compatibility mode).
Booting  the (normal) Linux Mint 17.1 Cinnamon 64-bit both crashed like booting Kubuntu 15.04.

See attached lshw files.
How can I best upgrade these PC's to Kubuntu 15.04?

Thanks in advance!

---

### Post by Bucky Ball on 2015-04-26
When you boot from the DVD and get to the screen of options, i.e. 'Try Ubuntu', 'Install Ubuntu', etc., hit F6 key. You should get some options pop-up. Choose 'nomodeset'. Proceed. Any different?

Sounds like a graphics issue.

(PS: Not sure what is in your attached files but better to put terminal output between [code] tags and just post that. Not everyone is willing to download files from total strangers (no offense intended) so might improve your chances of getting support.)

---

### Post by Rob Sayer on 2015-04-26
I use Mint/Cinnamon and having to use Compatibility mode indicates hardware support issues.  Try booting the 15.04 iso with the nomodeset parameter, as this kind of sounds like graphics adapter problems.

My next question is ... why do you need 15.04?  It is *not* a long term support release.  I won't install anything but an lts release unless I have hardware support issues.

Try finding the video adapter from your machines from the lshw texts and doing a web search for ubuntu 15.04 (or just ubuntu) and the video card.

---

### Post by Bucky Ball on 2015-04-26
> **Rob Sayer said:**
> Try booting the 15.04 iso with the nomodeset parameter, as this kind of sounds like graphics adapter problems.

Exactly what I stated and explained how to do in post number two. ;)

I was wondering why OP was using 15.04, though, but people have their reasons. I stick to LTS for my main squeeze also.

---

### Post by hjvdmolen on 2015-04-26
Guys, thanks for your swift reply.
Unfortunately, hitting F6 at that stage doesn't seem to do anything, and it isn't clear how I can boot the iso with the nomodeset parameter.

However, I managed to switch off the desktop effects at the "Try / install" screen with Alt-Shift-F12.
The "Try Kubuntu" option then produces a distorted desktop and hitting Alt-Shift-F12 again gets me a normal desktop.

So it looks like a graphical issue - however both my PC's use the graphic chips on the motherboard, which worked OK in Kubuntu previous versions.
It seems like in the latest Kubuntu version some graphical drivers were removed.

---

### Post by Bucky Ball on 2015-04-26
Good one, but odd about F6 showing no options. Perhaps it is somewhere else now (haven't checked out 15.04 so don't know what changes have been made).

Get online and:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... or use the Software Updater, if you haven't already. Reboot and see how you go. Same issue, perhaps have a look in 'Additional Drivers' and see if there is something there pertaining to your video card you could install and try (you may need to go into Software & Updates and enable the Canonical Partners and Proprietary third-party drivers repos for this). If not, let us know where you're up to.

---

