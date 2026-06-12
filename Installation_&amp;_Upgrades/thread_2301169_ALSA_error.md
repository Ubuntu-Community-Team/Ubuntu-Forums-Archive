---
title: "ALSA error"
date: 2015-10-31
forum: Installation &amp; Upgrades
---

### Post by Ahunt on 2015-10-31
I had a flawless installation of Lubuntu 15.04 running on both my laptop and desktop computers. I upgraded both to Lubuntu 15.10 this past week using the update process. The laptop upgraded fine, with no problems at all, but the desktop developed some issues. The main issue is that the audio now crashes constantly with the error "ALSA error: send_pcm_open failed: No space left on device." The 1GB hard drive is less than 12% full and the RAM never goes over 1.5 GB out of 6 GB installed. A reboot fixes the ALSA issue until it crashes again indicating that the hardware is not the issue.

After a few days of constant ALSA crashes I decided to do a fresh install of Lubuntu 15.10 from a DVD, on the desktop, but the same issue persisted in the new installation.

This may or may not be relevant, but this box used to boot Lubuntu 15.04 in about 55 seconds. On Lubuntu 15.10 it takes 2:40 most of the time and hangs up on the hardware boot screen. Occasionally it boots normally in about 57 seconds, but the ALSA crashes still occur regardless. During the DVD installation of 15.10 I received a Debian warning regarding EFI vs legacy boot. The desktop is a Gateway DX4860 tower that used to run Win7 and includes EFI boot, but was never upgraded to Win8 or UEFI.

Any thoughts on this would be greatly appreciated.

---

### Post by Ahunt on 2015-11-01
Just an addition piece of information: When an ALSA crash has occurred VLC returns the error: "Audio output failed: The audio device "default" could not be used:
No space left on device."

---

### Post by Ahunt on 2015-12-16
Just to sew this issue up, over time a series of kernel and firmware updates seem to have fixed the ALSA crashes and also the slow boots times. This can now be considered "closed".

---

