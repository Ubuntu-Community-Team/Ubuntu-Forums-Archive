---
title: "Ubuntu install fail on Dell XPS 15"
date: 2018-12-22
forum: Installation &amp; Upgrades
---

### Post by lpalazzotto on 2018-12-22
I have been having the same problem with a Dell XPS 15, tried to switch from RAID to AHCI and the PC could not even boot/reboot. It gave me errors until I switched back to RAID. Any ideas?

The errors where that Windows detected a problem and was shutting down (first time), then gave me either the option to shut down or advanced options (second time). I did not what to do with the advanced options: whether to keep UEFI on or off and restart in Legacy mode... I do not think that this is the problem anyway.

Any idea?

---

### Post by oldfred on 2018-12-22
You have to install AHCI drivers into Windows. Do not know details, but I think one of the Dell links discusses it. It should just be in the Dell Driver support download page.

---

### Post by lpalazzotto on 2018-12-23
I have been having the same problem with a Dell XPS 15, tried to switch  from RAID to AHCI and the PC could not even boot/reboot. It gave me  errors until I switched back to RAID. Any ideas?

The errors where that Windows detected a problem and was shutting down  (first time), then gave me either the option to shut down or advanced  options (second time). I did not know what to do with the advanced options:  whether to keep UEFI off and restart in Legacy mode or keep it on... I do not  think that this is the problem anyway (Ubuntu 18.04 can work with UEFI).

Any idea?

---

### Post by lpalazzotto on 2018-12-23
Ok, thanks. Let me try.

---

### Post by oldos2er on 2018-12-23
Posts moved to their own thread.

@lpalazzotto Please don't hijack others' threads, it's akin to interrupting people's conversations, i.e. rude.

---

### Post by lpalazzotto on 2018-12-23
@oldos2er So now users have two threads discussing the same issue: brilliant.

The process is explained in detail here and there is much more to know than just about switching from RAID to AHCI
[https://medium.com/@peterpang_84917/personal-experience-of-installing-ubuntu-18-04-lts-on-xps-15-9570-3e53b6cfeefe](https://medium.com/@peterpang_84917/personal-experience-of-installing-ubuntu-18-04-lts-on-xps-15-9570-3e53b6cfeefe)

---

### Post by oldos2er on 2018-12-23
> **lpalazzotto said:**
> @oldos2er So now users have two threads discussing the same issue: brilliant.

That's how it works around here, we're not a stack exchange style forum.

---

### Post by lpalazzotto on 2018-12-23
> **oldos2er said:**
> That's how it works around here, we're not a stack exchange style forum.

Very smart.

---

