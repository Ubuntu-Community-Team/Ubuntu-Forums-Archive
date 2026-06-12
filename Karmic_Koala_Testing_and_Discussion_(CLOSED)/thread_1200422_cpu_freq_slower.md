---
title: "cpu freq slower"
date: 2009-06-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cornflake000 on 2009-06-30
Here's my first and only Karmic question so far since the day it came out....

My CPU is running at a slower frequency than I have it set in my BIOS.  I don't run the CPU frequency utils or any other software controls.  I have a P4/3.4Ghz that I OC to 4.3 running with Jaunty64.  I run Karmic in a separate partition on the same machine.  In Karmic I noticed my temperature was way down so I checked the CPU to find it running at 2.8Ghz.  I switch back to Jaunty and boom 4.3 @ 39C which is expected.

Anyone have any idea why it clocks down in Karmic? 

Thanks.....

---

### Post by zika on 2009-06-30
> **cornflake000 said:**
> Here's my first and only Karmic question so far since the day it came out....

My CPU is running at a slower frequency than I have it set in my BIOS.  I don't run the CPU frequency utils or any other software controls.  I have a P4/3.4Ghz that I OC to 4.3 running with Jaunty64.  I run Karmic in a separate partition on the same machine.  In Karmic I noticed my temperature was way down so I checked the CPU to find it running at 2.8Ghz.  I switch back to Jaunty and boom 4.3 @ 39C which is expected.

Anyone have any idea why it clocks down in Karmic? 

Thanks.....Frequency scaling: ondemand instead of performance .. ?
sudo cpufreq-selector -c {0,1,2,...} -g {performance,ondemand}

---

### Post by tad1073 on 2009-06-30
How does one get it to stick after rebooting?

---

### Post by zika on 2009-06-30
> **tad1073 said:**
> How does one get it to stick after rebooting?
add it to **/etc/rc.local**.
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
cpufreq-selector -c 0 -g performance
cpufreq-selector -c 1 -g performance
cpufreq-selector -c 2 -g performance
exit 0
```
There are more "proper" ways to do this but this is the easiest to undo.

---

### Post by tad1073 on 2009-06-30
with a quad core it would look like this?
```

cpufreq-selector -c 0 -g performance
cpufreq-selector -c 1 -g performance
cpufreq-selector -c 2 -g performance
cpufreq-selector -c 3 -g performance

```

---

### Post by robert shearer on 2009-06-30
to monitor the cpu dynamically right click on a panel and choose
> add to panel
then scroll down to > CPU Frequency scaling monitor and add this.

Once it is on the panel you can see how the cpu is being scaled and if you mouse over it you will see the mode displayed (ondemand,performance etc)

---

### Post by tad1073 on 2009-06-30
> **zika said:**
> add it to **/etc/rc.local**.
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
cpufreq-selector -c 0 -g performance
cpufreq-selector -c 1 -g performance
cpufreq-selector -c 2 -g performance
exit 0
```There are more "proper" ways to do this but this is the easiest to undo.

Didn't work.

---

### Post by tad1073 on 2009-06-30
> **robert shearer said:**
> to monitor the cpu dynamically right click on a panel and choose

then scroll down to  and add this.

Once it is on the panel you can see how the cpu is being scaled and if you mouse over it you will see the mode displayed (ondemand,performance etc)

I monitor my system with conky. I would like to find a way to make the the scaling stick after a reboot.

---

### Post by robert shearer on 2009-06-30
I have** not** done this but here is another thread that may  have an answer,  read and consider if it applys to your situation.  (3rd to last post.) Quoted below....

[http://ubuntuforums.org/archive/index.php/t-1125148.html](http://ubuntuforums.org/archive/index.php/t-1125148.html)

> April 15th, 2009, 08:57 PM

This command should do what you want:
sudo cpufreq-set -g performance

If you want it to run at every boot, add it to /etc/rc.local (that script runs as root, so you don't need 'sudo' there). I think that'll do the trick.
If it doesn't work, maybe editing /etc/init.d/cpufrequtils and changing the GOVERNOR= line from ondemand to performance will.


also try..   
 ```
site:ubuntuforums.org cpu Frequency scaling
``` as a Google search.

---

### Post by zika on 2009-06-30
> **tad1073 said:**
> Didn't work.Sorry to hear that. It works for me. I will try to digg some deeper place where to change. Just give me the details of Your machine.
On the first thought, Go to System->Preferences->StartUpApps and uncheck something called CPU (whatever) ... That should do the trick. I do not have Jaunty handy ... :(

---

### Post by tad1073 on 2009-06-30
With 9.10, I believe that cpu frequency scaling is not modular, where as, it is built into the kernel and I don't have enough knowledge to compile and configure my own kernel.

---

### Post by zika on 2009-06-30
deleted by author ...

---

### Post by zika on 2009-06-30
deleted by author

---

### Post by Anubis on 2009-06-30
> **tad1073 said:**
> I monitor my system with conky. I would like to find a way to make the the scaling stick after a reboot.
He did not ask you what you monitor your freq. with. Did you even try the suggestion? Conky can't do what the applet he suggested can. If you are not even going to follow the suggestions given, why bother to post?

---

### Post by cornflake000 on 2009-06-30
> **robert shearer said:**
> to monitor the cpu dynamically right click on a panel and choose...

Once it is on the panel you can see how the cpu is being scaled and if you mouse over it you will see the mode displayed (ondemand,performance etc)

This doesn't work if your CPU is OC'd...

---

### Post by cornflake000 on 2009-06-30
OK... Skip my last comment.  It used to not work!  I have always had an error when booting which said the mod couldn't start because of unusual configuration or something.  I just tried it in Karmic and it runs just fine even OC'd with options to change performance.  The Jaunty and earlier do not give that option on my machines.

All is OK... Thanks!

---

### Post by cornflake000 on 2009-06-30
Well... stupid comes in 3's I guess...  You DO have the option to change performance in Jaunty.  I just updated the prog...

oh well...

---

### Post by robert shearer on 2009-06-30
OH, I've a lifetime of stupidity, buckets of it to spare! :)

Still willing to try things though, keeps me learning and stops the grey matter atrophying.:o

Glad to hear things are working.

---

### Post by zika on 2009-07-07
> **tad1073 said:**
> Didn't work.I think I've cracked it ...
Move the file **/etc/init.d/ondemand** somewhere safe (everywhere but not in the */etc/init.d/)* or (even better so You can undo this easily) revoke its e_X_ecute privilege ...```
sudo chmod -x /etc/init.d/ondemand
``` or to undo ```
sudo chmod +x /etc/init.d/ondemand
``` ...
**update:** Tweak given above works. The only problem is that on shutdown it might make some delay because it is "missing". The other solution is to edit that file and to change the line ```
echo -n ondemand > $CPUFREQ
```into```
echo -n performance > $CPUFREQ
```.

---

