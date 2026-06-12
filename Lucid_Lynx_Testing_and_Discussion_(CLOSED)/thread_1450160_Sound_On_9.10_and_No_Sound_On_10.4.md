---
title: "Sound On 9.10 and No Sound On 10.4"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by shadowfax1 on 2010-04-08
I've got 9.10 and 10.4 on a dual boot.  My sound works fine on 9.10 but has no sound on 10.4.  It's configured exactly the same way on both os's.

Soundblaster

---

### Post by scouser73 on 2010-04-08
I know this seems silly, but have you checked that the sound preferences aren't muted? I say this because I had the very same problem when I installed 10.04 and found that the volume was set to mute.

---

### Post by shadowfax1 on 2010-04-08
Thats the first thing I checked...All the mute boxes are unchecked.

---

### Post by jscuster on 2010-04-09
Hello,
I have the same problem. Upgraded from 9.10. I am using the netbook remix on a gateway lt2104U.
Any suggestions?
I am blind and using orca, so no sound is especially bad for me. I had sound on the live cd, but no sound after install.

Thanks

---

### Post by shadowfax1 on 2010-04-09
Shows the driver installed and working correctly...must be a bug issue!
Hopefully by the 29th they would have worked it out!

---

### Post by MBHAKM on 2010-04-09
Choose the output connector = Analog speaker under sound Preferences.
This should work.

---

### Post by the.scarecrow on 2010-04-09
I also have this problem. My sound was working okay with Beta 1, but running Beta 2, my sound no longer works.

I am using a Dell D600 laptop with a Sigmatel 9750 Audio Controller. Running the System>Administration>System Testing, audio tests, correctly identifies the sound device as:

0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with STAC9750,51 at irq 5

This is exactly the same result as in Karmic where the sound does work.

However none of the following audio tests produce any sound output and the software does not seem to respond to any microphone input.

> @MBHAKM  	
Re: Sound On 9.10 and No Sound On 10.4
Choose the output connector = Analog speaker under sound Preferences.
This should work.

This option no longer/does not appear to exist or at least I can't find it.

---

### Post by the.scarecrow on 2010-04-09
There is a fix/work around in this thread

[http://ubuntuforums.org/showthread.php?t=1450122](http://ubuntuforums.org/showthread.php?t=1450122)

---

### Post by shadowfax1 on 2010-04-11
Well Beta 2 solved the sound issue for me...

---

