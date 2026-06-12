---
title: "Can't play via A2DP to Motorola S805 headset"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by xak on 2010-03-08
On Lucid Alpha3 (fully updated today), I am having trouble using my Motorola S805 Bluetooth headphones. I also have a Belkin Bluetooth Music Receiver at home which works flawlessly (in fact, I was blown away with how easy that was using the new Bluetooth and Sound Preferences panels!).

With the Motorola S805, they pair fine using the Bluetooth applet, but an Output device never shows up in the Sound Preferences panel to send audio to them. Also, I was getting "AVRCP: failed to init uinput for <MAC address>" in syslog until I did a 'modprobe uinput', now this does not appear in syslog, so presumably the buttons for the headset would work if A2DP was successfully working.

Since I skipped using Karmic, I am unfamiliar with the new PulseAudio and Bluetooth integration (in Jaunty, I had to use a set of hacky shell scripts to get audio, and it was very unreliable). Could someone point me in the right direction for getting PulseAudio to see the S805 on Lucid? Thanks!

Let me know if any logs or additional info are needed, and I'll gladly post them.

**SOLUTION:**
It seems that the latest round of package updates today have solved the issue! The last step once the device was detected by Pulseaudio was to enable A2DP stereo instead of HSP/HFP mono, and this can be done on the Hardware tab of Sound Preferences.

---

### Post by xak on 2010-03-24
I reinstalled from scratch with Beta 1 and the problem persists. Any suggestions on how to troubleshoot this?

Thanks!

---

