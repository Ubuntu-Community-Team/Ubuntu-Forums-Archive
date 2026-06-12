---
title: "boot partition filling up with kernel images"
date: 2014-08-06
forum: Installation &amp; Upgrades
---

### Post by Lasse_Kliemann on 2014-08-06
This is a known problem: /boot will run out of space after some time, due to obsolete kernel images. It will only become evident when /boot is on a separate filesystem, as it is the case for encrypted systems.

Can anyone confirm whether this has (finally!!) been fixed in 14.04? If so, ignore the rest of this post.

Otherwise. Please let us find a solution for this ridiculous design error.

The general recommendation is to run a chain as follows:

1.) dpkg --get-selections to get all installed packages
2.) grep out kernel images
3.) remove the current kernel from the list, based on uname -r
4.) run apt-get remove on the remaining ones

This may be OK if run semi-automatically. But I need it to run completely unattended, alongside completely unattended system upgrades. (Because I'm preparing a system for a non-tech person who has better things to do than to care about old kernel images.)

In combination with an unattended system upgrade, the following could happen (I imagine):

1.) let the current kernel be version N
2.) a new kernel is installed, say version M
3.) the above procedure is run, but uname -r still gives version N, so version M is removed again
4.) FAIL

One idea of mine was to sort the list of kernels lexicographically and then remove all but the, say, last 2 in the list. (And also remove the one given by uname -r from the list.) This way the latest kernels would never be removed. That is, IF lexicographical ordering puts the latest kernel last. Which, by looking at past package names, appears probably not to be the case. m(

So the next idea is to write a more sophisticated kernel version parser.

Any ideas? Has anyone already implemented a working solution?

Thank you!

---

### Post by oldfred on 2014-08-06
Someone posted this, but I downloaded some others that are muliti-line that I can understand. :)

 # one line purge
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge

two line version:
#OLD=$(ls -tr /boot/vmlinuz-* | head -n -2 | cut -d- -f2- | awk '{print "linux-image-" $0}')
#if [ -n "$OLD" ]; then sudo apt-get -q remove --purge $OLD; fi

I usually just use synaptic, but if you need command line then several scripts have been posted.

I downloaded and used one, but the variable for number to keep did not work. I think I fixed it but do not remember or if I tested it. I always want to keep two and it only kept one, not matter how you set it.

I can just post one or the other I downloaded if you like.

---

### Post by sedawk on 2014-08-06
You are absolutely right, that a tool has to deal with a M>N situation where N is the running kernel - it should not remove newer M.
So what is needed is a sorted list, older versions first, and a tool that removes older entries (<N) but stops at N and therefore also ignores anything >N.
A very simple approach to get such a sorted list is to sort the relevant files in /boot by timestamp, oldest first.
But timestamps are not as reliable as the version numbers. Sorting by version numbers can be done with tool "sort". I think "sort -V" is the way to go.

---

### Post by Bashing-om on 2014-08-06
> **sedawk said:**
> You are absolutely right, that a tool has to deal with a M>N situation where N is the running kernel - it should not remove newer M.
So what is needed is a sorted list, older versions first, and a tool that removes older entries (<N) but stops at N and therefore also ignores anything >N.
A very simple approach to get such a sorted list is to sort the relevant files in /boot by timestamp, oldest first.
But timestamps are not as reliable as the version numbers. Sorting by version numbers can be done with tool "sort". I think "sort -V" is the way to go.

As of release 13.10 (EOL now) that functionality is built into "autoremove".
```

Sudo apt-get autoremove

``` now removes those older kernels ( images and header and related files too ), leaving the current kernel and also 1 latter kernel.

As to whether it also works in "encrypted systems" I do not know from direct experience. But, it should.

A case of the developers hearing their community !

---

### Post by oldfred on 2014-08-06
One of the scripts checks the linked files which with Debian based systems have links to the most current kernel & second most recent. But I have had cases where the links are broken.

# Make a list of the kernels to keep. These are the kernels linked to by /vmlinuz,
# /vmlinuz.old, and the currently running kernel.
keepList="$(readlink -q /vmlinuz) $(readlink -q /vmlinuz.old) boot/vmlinuz-$(uname -r)"

---

### Post by ian-weisser on 2014-08-06
> **Lasse_Kliemann said:**
> This is a known problem: /boot will run out of space after some time, due to obsolete kernel images. It will only become evident when /boot is on a separate filesystem, as it is the case for encrypted systems.

Can anyone confirm whether this has (finally!!) been fixed in 14.04? 

It's not a design problem. It was never a design problem.
Last time I checked, the problem was due to several different bugs, each of which had been fixed in 14.04
Most of the important discussion is at [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/923876](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/923876)

When apt installs a kernel, a hook script, /etc/kernel/postinst.d/apt-auto-removal , marks the package as ineligble for autoremoval, and non-running older kernels as eligible for autoremoval. Then all older kernels (except the current one and the new one) get autoremoved the next time you update.

Back in November 2013, this was all fixed and pushed out. Pre-bugfix kernels would not be autoremoved, but everything after would.
 Sure enough my old kernels autoremove properly, but I don't have a separate /boot.

So, since some 14.04 users with separate /boot partitions seem to be suffering from this problem again, either one of the bugfixes was incomplete, or another bug is out there. So far, none of the bug reports on Launchpad seem to have enough information for me or another triager to reproduce the problem.
For example, I haven't seen any bug reports that specify /boot . Had any done so, I would have tested that way.
Regrettably, for this month I won't be able to test the separate /boot hypothesis, so someone else will need to carry that ball.

---

### Post by Lasse_Kliemann on 2014-08-07
Thanks everyone for replying so quickly. This problem probably being fixed by now is good news. I have set up a 14.04 desktop today with a separate /boot and am watching closely what happens. I'll report back here.

---

