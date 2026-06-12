---
title: "Grub rescuce - Can not load module"
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by FizzerJE on 2011-07-01
This is my fourth variant of trying to get Ubuntu installed and i have lost how mant different steps of troubleshooting I have done.

I could attach a long list of specs but will wait for someone to request what thewy need. At the Livecd Enviroment ATM

I have gone back to a basic partion layout because i thought Raid1 > LVM may be causing issues.

Now installing on a single 750GB Drive:
Partioned
4GB - Swap
50GB /
rest /home


Every install drops me at the grub rescue> prompt.

I can boot the livcd I installed from no problem.


Grub rescue troubles:

I can ls and find the partions of the drive lablled

(hd0,msdos3) - home partion
(hd0,msdos2) - root partion
(hd0,msdos1) - swap area


ls (hd0,msdos2)/boot/grub - Lists the .mod's  and both Linux and normal are there.

Issue comands:

set prefix=(hd0,msdos2)/boot/grub
set root=(hd0,msdos2)

insmod normal
Error 'Invalid object type'

insmod linux
Error 'Invalid object type'


Tried to point via full path

insmod (hd0,msdos2)/boot/grub/normal.mod   [I]ALSO [/I ]linux.mod

Brings back the same error.
Error 'Invalid object type'

Tried to load from /usr/lib/grub/i386-pc

Again! gives the same error.

I am to say the least getting confused and frustrated.

Off to walk the dog to the pub and grab a beer to chill a bit.
Will be back shortly, hopefully with some help awaiting.

:)

---

### Post by YesWeCan on 2011-07-01
Four failed attempts? What a pain.
A little info about your set-up would be good. PC or laptop, type, age, IDE/SATA disk, Ubuntu version?

It may help if you could download this and run it and post RESULTS.txt here:  [FONT=Nimbus Sans L, sans-serif]BootInfoScript: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)[/FONT]

---

### Post by FizzerJE on 2011-07-01
Thanks for pointing me the the script. Will keep that one handy.

As for the Grub Issue.

Apologies would have responded sooner, but hitting away at a degraded software raid array, that would not start 'Inactive' and trying to work out why the hell Ubuntu has decided to rename all my arrays from md0..  to md127

The problems I have had with Ubuntu have done my head in...  :p


Never got the Boot Loader working from the rescue enviroment.
I can't actually understand why it has the issue in the first place...... All the other distros including Chakra (Ubuntu based) have installed fine.

The boot issue happens on 10.04 10.10 and 11.04


Downloaded [Boot-Repair Here!]("https://help.ubuntu.com/community/Boot-Repair") from within a LiveCD.

HAVE NOT found out why I get **Invalid Object File** on the insmod.
So it is still not solved.


I do not like to do stuff that way, would rather pound the problem out, but wasted too much time trying to get a running system.
Having to come to ubuntu kicking and screaming TBH, as I have not been able to get XBMC running on CentOS5.

I have to use Cent for my studies, and Debian based systems don't help for the RHCT.

Not too impressed  :(

Sorry for rant..

Lol

Whole well.  Now sound over HDMI and work out where I have to insert my luks encrypted auto unlock script for boot.

Joy Joy

---

### Post by FizzerJE on 2011-07-02
Well as I am having a few issues with 11.04...

Want to roll back to 10.10, as what I have read it is a little more 'Working'

Now, it is bugging me, the insmod issue.

About to try a different install disk *10.10 Livecd Desktop x64*

I wanted to get the info for you as I am sure Grub will not install correctly again :) but having a run error on the script.

[B]boot_info_script.sh: 353: Syntax error: "(" unexpected (expecting "fi")
[/B]

```
349 
 350 if [ ${this_BIS} -eq 0 ] ; then
 351    declare -a BIS_files;
 352 
 353    BIS_files=( $(ls "$(dirname "$0")/boot_info_script.sh" "$(dirname \"     $0\")"/boot_info_script\(*\).sh 2> /dev/null) );
 354 
 355    if [ "${#BIS_files[*]}" -ge 2 ] ; then
 356       printf 'Multiple boot_info_script files where found:\n\n';
 357 
 358       for i in ${!BIS_files[@]} ; do
 359         eval $(echo 'BIS_'$(grep -m1 '^VERSION' "${BIS_files[$i]}") );
 360         printf "  - ${BIS_files[$i]}:\tversion ${BIS_VERSION}\n";
 361       done
 362 
 363       printf '\nAre you sure you want to run this version? If so, run:\     n\n  bash %s --this %s\n\n' "$0" "$*";
 364       exit 1;
 365    fi
 366 fi

```

As far as I can see, all the IF statement previous to the error line are closed, so not sure on where it is has an open if.
My scripting is far from knowledgeable YET  :)

---

