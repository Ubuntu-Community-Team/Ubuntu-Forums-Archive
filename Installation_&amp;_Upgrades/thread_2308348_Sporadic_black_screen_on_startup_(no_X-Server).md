---
title: "Sporadic black screen on startup (no X-Server?)"
date: 2016-01-02
forum: Installation &amp; Upgrades
---

### Post by kuv02 on 2016-01-02
Hi guys,

after fixing an unbootable system ([boot partition full. Last kernel update was unable to install.]("http://ubuntuforums.org/showthread.php?t=2302981")) my uncle told me that sometimes (like once every 4-10 boots) the system will not boot into KDE but stay in a blackscreen for several minutes.

I tried to reproduce this behaviour by restarting the laptop again and again and could see this behavior too.

When the Blackscreen (simply a complete black screen. No cursor. Nothing) appears, I could switch via Ctrl+Alt+F1 into the console. There I was able to login. So the system itself is there. "Only" the GUI is not booting.

Could you give me some dignose steps to run through? What should I check to find the problem? (I'm still at Beginner level and would be happy about a checklist/procedure to follow)

---

### Post by Dreamer Fithp Apprentice on 2016-01-02
Not a fix, but a possible step toward diagnostis:
When you get a console try ```
startx
```

---

### Post by kuv02 on 2016-01-23
Hi I'm back. I tried your suggestion. 
This is what happened:

1. rebooted until problem showed up
2. switched to runlevel 1(is this how you call it? ALT+CTRL+F1)
3. > startx
4. a Xserver startup printout appears. 1-3 seconds later the display turns of (no backlight), still some seconds later I hear the "welcome sound" (or some other sound)
5. I was unable to turn the display on. So I thought, maybe the wrong display is configured as default (HDMI) but I could switch to runlevel 2 (Alt+Ctrl+F2) and log in via console.

So I rebooted until I got to the inital blackscreen. Than.
1. log in to Runlevel1
2. pluged in a HDMI cable to my TV
3. imideally a ERROR Log was printed into the console(!) I didn't enter anything. Never seen something like this.
This was the error log:
```
[drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
[drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
[drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
[drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 116
[drm:drm_edid_block_valid] *ERROR* Raw EDID: ...
```

After unpluging and repluging the HDMI cable the EDID Error showed up every time.

Sometimes the computer boots sucessfully. So I can access all the tools to analyse this problem, but I don't know where to look and what to look for. So I need help from you guys. Tell me what I should check out and I write what I found here.

---

