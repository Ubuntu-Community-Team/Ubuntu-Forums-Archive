---
title: "Firefox Update Broke Noscript"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by linux4me on 2008-02-08
I just ran the update in Update Manager to Firefox 2.0.0.12 which appeared to go smoothly until I did the restart of Firefox.

At that point, Firefox failed to restart after giving me an error message that Noscript was not properly functioning and needed to be reinstalled.

I was finally able to get Firefox to start from Terminal, though the first attempt gave me a Segmentation fault (core dumped) error, it started the second time.

Now I have uninstalled and reinstaleld Noscript, but Noscript doesn't run and though it appears to be installed correctly in the Add-ons dialog, when I try to change preferences the 'OK' button does nothing; i.e., doesn't close the window and save the changes.

I miss Noscript! Has anyone else encountered this and found a fix?

---

### Post by argle on 2008-02-08
I have also encountered this problem, exactly as you described.
Running firefox as super user did not fix the problem either (and in some cases also gave the segmentation fault).  
Disabling all other installed extensions also did not get noscript working.

---

### Post by linux4me on 2008-02-08
I found the cure, for me at least. 

I removed NoScript, restarted Firefox, and it was still acting weird, giving me the segmentation fault intermittently when started from terminal and only starting from the toolbar icon occasionally, other times failing silently.

I removed Colorzilla restarted Firefox and Firefox behaved again. I tried installing NoScript, and now NoScript works. I will miss Colorzilla, but I don't know if I will risk installing it again...

---

### Post by argle on 2008-02-08
Thanks!  Removing colorzilla worked for me, too!  And then I found these instructions which got it working again (concurrently with NoScript!)

It's probably related to this thread:
[http://ubuntuforums.org/showthread.php?t=271159](http://ubuntuforums.org/showthread.php?t=271159)

with the fix summarized at the top of this discussion:
[https://addons.mozilla.org/en-US/firefox/discussions/comments.php?DiscussionID=1727](https://addons.mozilla.org/en-US/firefox/discussions/comments.php?DiscussionID=1727)

as follows:
* Uninstall ColorZilla
* Download latest Firefox binaries from [http://www.getfirefox.com/](http://www.getfirefox.com/)
* Unpack (tar -xvzf firefox.....tar.gz)
* cp firefox..../libxpcom* /usr/lib/firefox/
* Reinstall ColorZilla
* Restart Firefox and eyedropper should now work
... with noscript.

---

### Post by linux4me on 2008-02-08
Worked like a charm! Thanks, argle.

Seems like I had to do something like that the first time I installed Colorzilla.

---

### Post by mriendea on 2008-02-09
I had this same problem with Gutsy 64. Running firefox -g showed it was libnss. I re-installed libnss3-0d from synaptic, which fixed it.

---

### Post by Niniel on 2008-02-09
Thanks for the fixes... Funny this is only a problem in Ubuntu, not Windoze.

Update: Looks like it's sufficient to uninstall Colorzilla, restart FF, reinstall Colorzilla, and reboot again. Well, at least the symbols are showing up... but Colorzilla doesn't support eyedropper mode (anymore). Oh well, hopefully, this fill be fixed soon.

---

### Post by linux4me on 2008-02-10
Niniel,

Did you try following argle's steps for getting Colorzilla to work? My eyedropper mode is working in Gutsy.

---

