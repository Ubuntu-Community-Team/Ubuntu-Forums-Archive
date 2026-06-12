---
title: "edgy tweaks for mass install"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by skullmunky on 2007-01-28
hi,

i have a few questions which are probably, technically speaking, Admin q's but i'm posting here because they relate to installing & configuring a small fleet of workstations.  i've been running suse for the last 5 years or so, looking to upgrade, had a great experience with kubuntu & xubuntu on some home laptops and so am thinking about moving my work environment to kubuntu edgy too.  but, i'm hoping to get some quick pointers on a few things i'll need to do to customize the installs; these are things which i know how to do in yast, but couldn't quickly find easy configuration options for in kubuntu's config tools.  also i can probably figure out how to do most of these from the command line, of course, but i'm looking for Fast & Easy here - i'm an admin by necessity, not by choice (or by pay! :)  so always looking for quick ways to do things and clean GUI ways to do things that i can delegate to other people :)  

ok, so here's the list.  point me to other threads or howtos, please... and, sorry for being too lazy to search myself, again, very little time available to work on this stuff, so thanks for any help!  

1. NFS + NIS client authentication.  is there a gui tool for setting up mounts for NFS shares and for NIS authentication?

2. passwordless logins.  yes, i know, not a good idea.  real quick, here's why: this is in a school, 99% macs, students are used to being able to just come in, sit down, use computer, without needing to know passwords and so on.  i'd like to promote linux use, not prevent it, so the fewer barriers the better.  the usual suggested solution is to do an auto-login, which won't work for me because in addition to a general-purpose "student" account, some users have individual NFS shared accounts.  

3. netatalk + afpd + zeroconf (rendezvous) : is there a gui config for that?  

4. how to install a lot of stuff right off the bat? : ubuntu has a more minimal and tidy install than suse, which seems to take an everything-but-the-kitchen-sink approach.  i like the ubuntu way, but on the other hand since this is a whole bunch of machines i'm administering i'd like to get as much installed as possible at the beginning.   i feel like there's an easier way than individually apt-getting every little thing - maybe some metapackages or selection groups or something?  anyway here's what i want, more or less:

- kde desktop, but with GIMP and Firefox
- C,C++,Python,Perl, libs and dev tools, headers and libs for OpenGL development, Java, Eclipse, weird build alternatives like scons and gmake, 64 and 32 bit libs, cvs and svn, cervisia, and whatever else one would need to do development work with, say (1) game engines and 3D visualization, (2) java for cellphones, (3) computer vision (e.g. openCV), (4) microcontrollers (PIC or AVR).
- Pure Data, SuperCollider, JACK, Audacity, Cinelerra
- win32 codecs and libdecss, mplayer and vlc

5. ntfs / hfs+ support: i haven't been following these too closely, but does anyone know if we're close to the point that i can comfortably have students use external drives without reformatting to FAT?  (yeah, i know that's not even a ubuntu question.  the next one will be, i promise)

6. Adobe Utopia - a font unincluded and frowned upon for its legal entanglements, which is fine, except i have one old and weird piece of binary-only SGI graphics software that absolutely requires it.  Any fast way to get this installed?   i did it by hand somehow and of course can't remember what i did but it involved copy and pasting lines into some font cache file somewhere from a working suse distro.  

7. Also not Ubuntu specific, but maybe someone here knows.  I want to add some optional actions to the login screen - specifically, one to restart all network services.  What? Why?  people unplug the ethernet cables all the time to use their laptops in this lab.  that wrecks the nifty NIS/NFS login scenario; particularly if the machine is rebooted while the ethernet cable is unplugged, the NIS client won't bind and even if the network becomes available later it's too late. 

so i'd like to just add an option to restart those services.  or what would be even clevererer would be to make it so that making the network available tells the nis bind to try again.

8. XFCE - can you disable the alt+drag window shortcuts?  these make Maya unusable; i can disable them in Gnome and KDE, but the instructions for XFCE don't seem to work...

thanks!  

--skullmunky

---

