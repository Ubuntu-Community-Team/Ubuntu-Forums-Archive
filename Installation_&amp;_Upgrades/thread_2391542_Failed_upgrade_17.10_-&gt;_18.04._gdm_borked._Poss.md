---
title: "Failed upgrade 17.10 -&gt; 18.04. gdm borked. Possibly GPU drivers?"
date: 2018-05-10
forum: Installation &amp; Upgrades
---

### Post by palteater on 2018-05-10
Greetings

Computer: A HTPC with a non-overclocked Pentium G3256. No graphics card - using Intel integrated. Ran fine with 17.04 & 17.10.

I did:
sudo apt udate
sudo apt upgrade
sudo apt dist-upgrade
sudo apt autoremove
sudo do-release-upgrade

...and the thing did its thing for an hour. 

Then after the reboot, I get the Ubuntu logo, one of the purple dots ligh up, then I get a slowly flickering screen. Mostly black, occasionally showing the boot list - the rows of [  OK  ] Blah blah - that flashes into visibility for a split second and then disappears.

So I filmed it and froze the video and it seems to get stuck on:

[  OK  ] Started GNOME Display Manager. Dispatcher Service....ystem changes.pp link was shut down...

Yes, it does say "ystem" there.

It doesn't react to CTRL+ALT+F1, F2, F3, etc - but it does reboot for a CTLR+ALT+DEL. If I whack the buttons frantically.

So I rebooted into GRUB (holding SHIFT during boot) and tried the root CLI. Didn't quite know what to do there, but found that apt commands generally failed. No access to database blah blah. 

So I booted into recovery mode instead. This time I could CTRL+ALT-F2 into console, but every three seconds the system would apparently try restarting the X server or something, because I had to CTLR+ALT-F2 repeatedly to get back to my console and continue doing things. This time apt commands worked, but all I found was that everything supposedly installed as intended.

"systemctl stop gdm" stopped the intermittent terminal switch/flicker thing.

Tried reinstalling gdm:
sudo apt purge gdm gdm3
sudo apt install gdm3 ubuntu-desktop
systemctl restart gdm

No difference.

Tried "sudo apt install xserver-xorg" but had the latest version.

Tried appending "nomodeset" to grub. The difference was that it stopped flickering at the [ OK ] row and instead only flickered a single top row of:

"/dev/sda1: clean, 163518/1703969 files, 2214867/6811392 blocks"
I interpret that as just a general message, not something ominous.

Where do I go from here? I assume there may be clues in the many MANY bytes of /var/log/ files?

cat /var/log/Xorg.0.log | grep "(EE)" 

gives me some rows about failing DRI. That sounds important. It also complains about missing GLX, which sounds less important. I somehow recall that GLX is for 3D whereas DRI is for 2D or some such? 

Anyhow, that sounds like failing X drivers. Can I force-install Intel drivers or something?

Grateful for any clues.

---

### Post by palteater on 2018-05-10
Tried uncommenting the /etc/gdm3/custom.conf "WaylandEnable = false" - no difference.
Tried apt purge gnome-screensaver as others on google had that problem. No difference.

I find references to the same problem going back to 2009 and older. All tried different things which worked for them. None for me so far.

---

### Post by QIII on 2018-05-10
Just as a note (I fixed your title) -- in the tech community the term "borked" is perfectly fine.  

The term originates from the US Senate confirmation hearings for Judge Robert Bork's nomination to the Supreme Court of the United States.  He got handled rather roughly.

Anyway, in the tech world, "borked" means "broken as a result of inattention, ignorance, naivety or negligence of the user."

"I just changed all the permissions on my entire / partition and borked my system!"  is just fine.

Cheers!

---

### Post by palteater on 2018-05-11
Oh really? :) I had no idea. English is not my primary language, I sometimes get idioms and colloquialisms wrong like that.

I thought it was derived from hackerish, like "1337 haX0rz". That it came from "broken", which hastily written became "br0ken" (because zero is next to oh) which became "b0rken" (because hasty writing and index finger being shorter), and stuck in the lingo as a humorous word.

Thanks for the explanation!

---

### Post by palteater on 2018-05-11
I also coupled it to the swedish chef muppet, who threw away his utensils while singing "bork bork bork!" - and I kind of envision programs that fail like that.

---

### Post by QIII on 2018-05-11
> **palteater said:**
> Oh really? :) I had no idea. English is not my primary language, I sometimes get idioms and colloquialisms wrong like that.

I thought it was derived from hackerish, like "1337 haX0rz". That it came from "broken", which hastily written became "br0ken" (because zero is next to oh) which became "b0rken" (because hasty writing and index finger being shorter), and stuck in the lingo as a humorous word.

Thanks for the explanation!

Both of which are urban legend.  Here's the actual story.  I've been using "borked" since the Reagan Administration here in the US:

[https://en.wikipedia.org/wiki/Robert_Bork](https://en.wikipedia.org/wiki/Robert_Bork)

---

### Post by mc4man on 2018-05-11
You could try installing & switching to lightdm, this may allow you to get to the login/greeter & then see if gnome-shell is able to be run.
( gdm3 uses gnome-shell, lightdm doesn't

---

### Post by palteater on 2018-05-11
Thank you for your reply!

I ended up installing lightdm, and the login greeter thing works insofar that I can run lightdm. It offers several variants of Gnome too, but all of those just cause the display to blink in and out of existance and then return back to the login.

I enabled more verbous output, and it seems that there is a driver failure (?). I get a bunch of "GL helper exited with code 32512" and "GLES helper exited with code 32512" and "software acceleration check failed: Child process exited with code 1" and "gnome-session-binary CRITICAL, We failed but the fail whale is dead" and so on.

So I am about to read up on how to check the Intel drivers. 


"*In March 2002, the [Oxford English Dictionary]("https://en.wikipedia.org/wiki/Oxford_English_Dictionary") added an entry for the verb bork  as U.S. political slang, with this definition: "To defame or vilify (a  person) systematically, esp. in the mass media, usually with the aim of  preventing his or her appointment to public office; to obstruct or  thwart (a person) in this way.*"

Wow - no, this was not at all what I meant when I wrote that gdm borked... =/

---

### Post by palteater on 2018-05-11
I installed various glx-related packages according to instructions on the net (glxinfo was missing) and made a symlink like:

sudo ln -s /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 /usr/lib/libGL.so.1

Then I could login to Gnome, but it is in software accelerated mode.

I'm giving up.

---

### Post by garvinrick4 on 2018-05-11
Dont give up you will not like it at all don't feel beaten could just be upgraded and not clean install.
Download and burn to disk or USB and install in same partition. I had a problem way back with upgrade to new dist
and have done clean installs since.

---

### Post by palteater on 2018-07-29
Yeah, thanks, but I did a clean install instead and all is well.

---

