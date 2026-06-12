---
title: "Enabling realtime kernel in Intrepid (beta)?"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by pointfive on 2008-10-19
I'm attempting to get jack working in Intrepid beta. I'm following this guide: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation), which worked in Hardy.

The problem I'm having now is with installing the realtime kernel. When I try "sudo apt-get install linux-rt", I get this output:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-rt: Depends: linux-restricted-modules-rt (= 2.6.26.1.5) but it is not going to be installed
E: Broken packages

```

So then I try to install linux-restricted-modules-rt, but I get this:
```
The following packages have unmet dependencies:
  linux-restricted-modules-rt: Depends: linux-restricted-modules-2.6.26-1-rt but it is not installable
E: Broken packages

```

And when I try to install linux-restricted-modules-2.6.26-1-rt, I get:

```
Package linux-restricted-modules-2.6.26-1-rt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-restricted-modules-2.6.26-1-rt has no installation candidate

```

Does this all stem from the fact I'm using beta? That's what the first message seems to imply. But how is testing of the rt kernel to occur if this is the case?

Thanks for any guidance.

---

### Post by Stochastic on 2008-10-19
Intrepid is still undergoing construction on the RT kernel.

The rt kernel in the repos is a .26 version, whereas quite a while ago Intrepid was moved to .27 for numerous stability reasons (midi is also quite screwed up in .26).  Unfortunately the rt patch for .27 has yet to be completed to a stable point (I don't know any more details than that - so don't look to me for more info), but it is in the works.

For now your best best (and what I'm doing) is running the regular .27 kernel in Intrepid, and keeping a second partition with Hardy RT on for your mission critical sound applications.  Eventually you'll be able to run .27-RT (this may not be until a little while after Intrepid is released) but for now, it's not ready.

Welcome to the world of beta.

P.S. most intrepid discussions should be kept to the Development >> Intrepid section of these forums, but since this is likely to be an issue that everyone in this section of the forums will bump into at the end of the month, we'll leave it here.

---

### Post by pointfive on 2008-10-19
Thanks for the clarification, Stochastic. It helps to know those details. It's a good news/bad news answer... sounds like we can hope for better stability in the long run (a big part of the reason I chose to try Intrepid beta was that I was having a tough time getting my Jack apps to run well in Hardy), but we're in for a wait. Hopefully it won't be too long in coming, and will be worth it!

I'll keep future posts about Intrepid beta in the forum you pointed out. Thanks for Giving this newbie some direction. :)

---

### Post by eric71 on 2008-10-22
I've been following the Ubuntustudio mailing lists about this, and it seems a rt kernel has now been accepted into Intrepid. It seems it is not shutting down properly, and I'm not sure how things run as far as jack and midi, etc., but at least it seems there will hopefully be a rt kernel available for the Ubuntustudio release. Hardy is working so well for me, I don't mind waiting though.

---

### Post by pointfive on 2008-10-22
Thanks eric... that's great news! Hardy was less kind to me, so I'm anxiously hopeful that I'll have more luck with Intrepid once it's released.

And I'm keeping my fingers crossed that I'll be able to get ffado working in Intrepid. freebob is no good with my interface, and I was unsuccessful in building ffado on Intrepid beta. (It compiled but doesn't seem to see my firewire expresscard.)

Hopefully only a little more patience will be necessary.

---

### Post by jalonsom on 2008-10-22
Well, I don't know if you really need a RT kernel with Ibex.

The thing is that most of the RT stuff is already merged into the current kernel.

For me jack server is running in RT mode with standard kernel, I just had to set up proper RT permissions.

---

### Post by pointfive on 2008-10-22
> **jalonsom said:**
> Well, I don't know if you really need a RT kernel with Ibex.

The thing is that most of the RT stuff is already merged into the current kernel.
Hmm... interesting. I'd give that a try if I could get ffado working. Hopefully I'll be able to in the next few days.

> **jalonsom said:**
> For me jack server is running in RT mode with standard kernel, I just had to set up proper RT permissions.
Any chance you could point me at a guide for setting these rt permissions?

---

### Post by oskar2000 on 2008-10-22
+1
Can you post a source for that?

I'm waiting for them to put the rt patch in a standard distribution for like... forever now.

I already have the beta iso, but I was holding back trying it. I was thinking about going back to PCLOS from hardy since the rt-kernel constantly froze up since I upgraded from 7.10

---

### Post by jalonsom on 2008-10-23
The permissions are the same that you would have to set for a rt kernel.

Basically you have to have to edit the file /etc/security/limits.conf and add the following lines:

```

# rtprio
@audio - rtprio 90
@audio - nice -5
@audio - memlock 500000
```

I am not sure about the actual values, as I have seen others, for example as described in [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
```

Then you have to create a user group called 'audio' and add yourself to that group. You are now authorized to use rt features.

Then I rebooted, although I'm sure there is a way to apply these changes without rebooting.

That's it.

Maybe there are other RT features which are not avaliable in the standard kernel, I don't know, but this setup allows me to use my m-audio fast track pro with no xruns at 10ms latency, and with occasional xrun at 5ms

Hope it helps.

---

### Post by plun on 2008-10-23
> **jalonsom said:**
> The permissions are the same that you would have to set for a rt kernel.

Basically you have to have to edit the file /etc/security/limits.conf and add the following lines:

Maybe there are other RT features which are not avaliable in the standard kernel, I don't know, but this setup allows me to use my m-audio fast track pro with no xruns at 10ms latency, and with occasional xrun at 5ms

Hope it helps.

I tested to set pulse-rt to those values and permissions...:)

Generic 32 bits kernel running.

> 

I: main.c: **We're in the group 'pulse-rt', allowing high-priority scheduling.**
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: yes, can high-priority: yes


CAP_NICE fails....:confused:

Latency down to 20ms  ...:)

(Still have some underruns) 

Thanks for pointing to this wiki !

---

### Post by pointfive on 2008-10-23
Thanks for that, jalonsom. I'd seen that before, but I didn't know those were permissions. I thought they were memory thresholds or something.

Now before I ask, let me ask if I *should* ask... would it be appropriate to ask for help troubleshooting problems with ffado? Or since they're technically beta drivers and I'm running them on a beta OS, should I not even bother?

---

### Post by oskar2000 on 2008-10-23
Just post them in this forum... it's close enough to final. Chances are most issues will persist.

---

