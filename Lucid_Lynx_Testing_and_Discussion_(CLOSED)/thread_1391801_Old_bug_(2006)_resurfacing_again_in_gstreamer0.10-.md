---
title: "Old bug (2006) resurfacing again in gstreamer0.10-plugins-bad"
date: 2010-01-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2010-01-27
After today's upgrade, same problems as years ago: Rhythmbox, Totem, MultiMediaSystemsSelector, not working. Remedy:```
sudo mv /usr/lib/gstreamer-0.10/libgstlv2.so /usr/lib/gstreamer-0.10/libgstlv2.so.backup
```...

---

### Post by phenest on 2010-01-27
I haven't got that package installed as it seems to have dependency problems. How did you get it?

---

### Post by phenest on 2010-01-27
Sorry. For some reason I was waiting for it as an update. Perhaps if I tried installing it. Doh!

Erm, you are correct. They are no longer working.

---

### Post by zika on 2010-01-27
> **phenest said:**
> Sorry. For some reason I was waiting for it as an update. Perhaps if I tried installing it. Doh!

Erm, you are correct. They are no longer working.It was not a partial upgrade, a regular one. Just apply remedy 3+ years old... Ecerything is OK. I, even, configured audio for rt...

---

### Post by Psumi on 2010-01-27
> **zika said:**
> It was not a partial upgrade, a regular one. Just apply remedy 3+ years old... Ecerything is OK. I, even, configured audio for rt...

Let's just hope it doesn't stay like this for when final lucid comes out. Otherwise, we'll have a bunch of unhappy gstream...ers.

Not that I can run lucid currently.

---

### Post by SevenMachines on 2010-01-27
the lv2 plugin was enabled on update, if its broken i'll just disable it again, is there a bug number

---

### Post by SevenMachines on 2010-01-27
if theres any more specifics too, i had no problems with anything in testing

---

### Post by jppr on 2010-01-27
[https://launchpad.net/ubuntu/lucid/+source/gst-plugins-bad0.10/0.10.17-3ubuntu1](https://launchpad.net/ubuntu/lucid/+source/gst-plugins-bad0.10/0.10.17-3ubuntu1)

---

### Post by SevenMachines on 2010-01-27
it ESSENTIAL that you have the latest version of slv2 upgraded otherwise the lv2 plugin will completely break gstreamer so can you make sure you have libslv2 below

slv2 (0.6.6-2build1) lucid; urgency=low

  * No-change rebuild to pick up librasqal2 as transition from librasqal1
 -- SevenMachines <SevenMachines@yahoo.co.uk>

[EDIT] if its still broken with that version then let me know

---

### Post by zika on 2010-01-27
> **SevenMachines said:**
> it ESSENTIAL that you have the latest version of slv2 upgraded otherwise the lv2 plugin will completely break gstreamer so can you make sure you have libslv2 below

slv2 (0.6.6-2build1) lucid; urgency=low

  * No-change rebuild to pick up librasqal2 as transition from librasqal1
 -- SevenMachines <SevenMachines@yahoo.co.uk>

[EDIT] if its still broken with that version then let me know```
~$ sudo aptitude search slv2
i A libslv2-9                                                                             - A library for simple use of LV2 plugins                                                         
p   libslv2-dev                                                                           - Development files (headers) for SLV2 library                                                    
p   slv2-doc                                                                              - Documentation for SLV2                                                                          
i A slv2-jack
```
```
~$ sudo aptitude show slv2-jack
Package: slv2-jack
New: yes
State: installed
Automatically installed: yes
Version: 0.6.6-2build1
Priority: optional
Section: universe/utils
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 135k
Depends: libc6 (>= 2.3.4), libjack0 (>= 0.118+svn3796), libraptor1 (>= 1.4.19), librasqal2 (>= 0.9.17), librdf0 (>= 1.0.9), libslv2-9 (>= 0.6.4-1~), jackd
Description: Jack support for LV2 plugins
 LV2 is a simple but extensible successor of LADSPA plugins, intended to address the limitations of LADSPA which many applications have outgrown. 
 
 This package contains binary files.
Homepage: http://drobilla.net/software/slv2
``````
~$ sudo aptitude show libslv2-9
Package: libslv2-9
New: yes
State: installed
Automatically installed: yes
Version: 0.6.6-2build1
Priority: optional
Section: universe/libs
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 168k
Depends: libc6 (>= 2.4), libraptor1 (>= 1.4.19), librasqal2 (>= 0.9.17), librdf0 (>= 1.0.9)
Recommends: slv2-jack
Description: A library for simple use of LV2 plugins
 SLV2 is a library geared towards music and audio applications which makes the use of LV2 plugins as simple as possible. LV2 is a standard for plugins and matching host applications,
 mainly targeted at audio processing and generation. 
 
 This package contains the shared library for libslv2.
Homepage: http://drobilla.net/software/slv2

```Yes, it is till broken...
```
/usr/lib/gstreamer-0.10$ ls -lt libgstlv2.so.backup
-rw-r--r-- 1 root root 23168 2010-01-27 12:17 libgstlv2.so.backup
```

---

### Post by SevenMachines on 2010-01-27
thanks zika, could you report a bug on this, and if anyone else experiencing it could 'affects me too' it please.
with slv2 build1 the driver shouldnt be segfaulting, i'll see if its fixable or just disable it. Is this on i386 by the way, or amd64 too?

---

### Post by SevenMachines on 2010-01-27
and if anyone could get a stacktrace that would be magnificent!

---

### Post by SevenMachines on 2010-01-27
looks like this may well segfault, not on all machines or perhaps even most but should be disabled if thats the case. if someone who has the problem can install the gstreamer -dbg packages and run,
$GST_REGISTRY_FORK=no gdb gst-inspect-0.10

---

### Post by zika on 2010-01-27
> **SevenMachines said:**
> thanks zika, could you report a bug on this, and if anyone else experiencing it could 'affects me too' it please.
with slv2 build1 the driver shouldnt be segfaulting, i'll see if its fixable or just disable it. Is this on i386 by the way, or amd64 too?It was segfaulting. AMD_64.

---

### Post by SevenMachines on 2010-01-27
i've opened
[https://bugs.edge.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/513347](https://bugs.edge.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/513347)

theres a possible fix being built
[https://launchpad.net/~sevenmachines/+archive/release+1/]("https://launchpad.net/%7Esevenmachines/+archive/release+1/")

if someone with the bug can test out the new packages (once they've built) for me and tell me how it goes? and add any information you can to the bug report. thanks

gst-plugins-bad0.10 (0.10.17-3ubuntu2~sevenmachines1) lucid; urgency=low

  * debian/patches/20_get_valid_gobject_names.patch:
    - create valid gobject property names in lv2 modules to prevent
    segfaults on lv2 plugin on some setups. from gstreamer bugzilla

---

### Post by zika on 2010-01-27
> **SevenMachines said:**
> i've opened
[https://bugs.edge.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/513347](https://bugs.edge.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/513347)

theres a possible fix being built
[https://launchpad.net/~sevenmachines/+archive/release+1/]("https://launchpad.net/%7Esevenmachines/+archive/release+1/")

if someone with the bug can test out the new packages (once they've built) for me and tell me how it goes? and add any information you can to the bug report. thanks

gst-plugins-bad0.10 (0.10.17-3ubuntu2~sevenmachines1) lucid; urgency=low

  * debian/patches/20_get_valid_gobject_names.patch:
    - create valid gobject property names in lv2 modules to prevent
    segfaults on lv2 plugin on some setups. from gstreamer bugzillaNo. It still doesn't work. The same remedy helps me get RB, Totem etc. back. Should I reinstall old package or should I keep this (new) one?

---

### Post by SevenMachines on 2010-01-27
ok, i think i'll disable it then

---

### Post by zika on 2010-01-27
> **SevenMachines said:**
> ok, i think i'll disable it thenNO! It did not work when I installed it as a .deb. Now, I've added Your ppa and it reinstalled and it works! You can get such a support only in Ubuntu community! Great job!

---

### Post by SevenMachines on 2010-01-27
I was just about through uploading the disable :) That sounds promising, can someone else with the problem verify? add to the end of the bug report if your launchpad registered

---

### Post by SevenMachines on 2010-01-27
sadly i've just uploaded the disabled version to the ppa, give it a minute and i'll upload ~sevenmachines3 with the fix enabled for people to test

---

### Post by zika on 2010-01-27
> **SevenMachines said:**
> I was just about through uploading the disable :) That sounds promising, can someone else with the problem verify? add to the end of the bug report if your launchpad registeredI was typing like mad, knowing that You were to change... I'm happy that I've got to You before that...

---

### Post by zika on 2010-01-27
> **SevenMachines said:**
> sadly i've just uploaded the disabled version to the ppa, give it a minute and i'll upload ~sevenmachines3 with the fix enabled for people to testThis is happening too fast, even for me...

---

### Post by SevenMachines on 2010-01-27
it's a rush because if one plugin segfaults it brings down all of gstreamer and you end up with bugs filed on totem, rhythmbox, pidgin, and any other number of things. best to get it done sooner rather than later :)

---

### Post by zika on 2010-01-27
> **SevenMachines said:**
> it's a rush because if one plugin segfaults it brings down all of gstreamer and you end up with bugs filed on totem, rhythmbox, pidgin, and any other number of things. best to get it done sooner rather than later :)I totally appreciate that. Thank You!

---

### Post by zika on 2010-01-27
Bad news. A minute ago I did upgrade and there it was... New version of gstreamer0.10-plugins-bad. And, it is bad, again. So, did You upload the right version at last...?```
-rw-r--r-- 1 root root   27296 2010-01-27 19:01 libgstlv2.so
```

---

### Post by SevenMachines on 2010-01-27
what version are you on?
$apt-show-versions gstreamer0.10-plugins-bad

---

### Post by SevenMachines on 2010-01-27
and if you can run 
$gst-inspect --gst-disable-segtrap

---

### Post by zika on 2010-01-27
> **SevenMachines said:**
> what version are you on?
$apt-show-versions gstreamer0.10-plugins-bad```
~$ apt-show-versions gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad/lucid uptodate 0.10.17-3ubuntu2~sevenmachines3
```

---

### Post by zika on 2010-01-27
> **SevenMachines said:**
> and if you can run 
$gst-inspect --gst-disable-segtrapI've run ```
~$ gst-inspect-0.10 --gst-disable-segtrap >gst.txt
```

---

### Post by SevenMachines on 2010-01-27
seems lv2 isnt crashing gstreamer in that example but theres certainly something wrong woth lv2, i'll just disable it like debian

---

### Post by zika on 2010-01-27
> **SevenMachines said:**
> seems lv2 isnt crashing gstreamer in that example but theres certainly something wrong woth lv2, i'll just disable it like debianJust say if I could be of any further help...

---

### Post by SevenMachines on 2010-01-27
thanks for the help zika, i'm guessing this is why debian decided lv2 was too unstable to enable, its just such a big impact bringing down gstreamer. it was worth a try :)

---

