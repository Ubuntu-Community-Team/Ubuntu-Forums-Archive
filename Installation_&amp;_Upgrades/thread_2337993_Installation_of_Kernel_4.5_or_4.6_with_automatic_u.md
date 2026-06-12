---
title: "Installation of Kernel 4.5 or 4.6 with automatic upgrades"
date: 2016-09-23
forum: Installation &amp; Upgrades
---

### Post by Only1KW on 2016-09-23
Since upgrading to 16.04, I have had a lot of issues with my system hanging when putting it to sleep.  I've been doing some research on this, and the most common and relevant root cause of this that I have found is that kernel 4.4 has some known issues with power management and upgrading to 4.5 or 4.6 fixes this.  I'd like to install a stable version of one of these kernels on my system to see if it will work for me.

The issue that I'm hitting is I'd like to be able to add an apt repository to my system which contains one of these kernels so that if any new security updates come out for them, I don't have to manually track that and upgrade them.  However, I've had no luck finding a ppa for this, which seems odd to me since I can find a ppa for most any package I can think of that I want the latest version of and the Kernel should be the most prolific package out there.  In my research, everyone seems to suggest downloading the .deb packages from kernel.ubuntu.com and installing them, which I'd like to avoid for reasons stated earlier.  I did find the canotical-kernel-team ppa, but that doesn't seem to be recommended for stable builds and appears to be updated on a more regular basis than what I'd prefer.  Any other suggestions I can try?

---

### Post by izznogooood on 2016-09-23
I dont think you understand what you are asking for.

If someone should or is making this PPA, it kind of defeats your intended purpose. You would be trusting you kernel package to a 3rd party maker. Which in theory could put malicious code in to it.

The other part is what kernel is right for you? Again you would be putting this in someone else´s hands. What kernel version, when to update etc.

I am now on 4.7.4, and check for updates once a month manually.

---

### Post by Only1KW on 2016-09-23
I acknowledge those risks you point out are valid, but those are the same risks that anyone else also accepts when using a 3rd party ppa for any other package.  If the ppa is popular enough, most people typically accept the risk.  Whether or not they should is a huge discussion in trusted computing that I'd prefer not to get into here.

---

### Post by ian-weisser on 2016-09-23
> **Only1KW said:**
> those are the same risks that anyone else also accepts when using a 3rd party ppa for any other package. If the ppa is popular enough, most people typically accept the risk.

Popularity is an excellent measure of webzine article. Lots of popular click-bait articles written by unskilled hacks out there.
Popularity is a truly terrible measure of the quality and trustworthiness of the software recommended by that hack.

If you wish to try newer kernels, follow the Ubuntu Kernel Team. Helping the Kernel Team to test new kernels and make them stable will get you much father than random online hacks and dodgy, untrustworthy sources.

---

### Post by Only1KW on 2016-09-23
Can you provide a better measure of quality and trustworthiness that doesn't require me to spend hours (probably days actually) reverse-engineering what I download?

---

### Post by ian-weisser on 2016-09-23
Already suggested - Use the products of the Ubuntu Kernel Team: [https://wiki.ubuntu.com/Kernel](https://wiki.ubuntu.com/Kernel)

Trying different kernels randomly in the hopes one is compatible with your hardware seems rather a waste of your effort.
Locate and subscribe to (or report) the relevant kernel bug. Help test the fix. Track the bug through the fix process. KNOW that it works and is fixed.

---

### Post by izznogooood on 2016-09-24
> **Only1KW said:**
> Can you provide a better measure of quality and trustworthiness that doesn't require me to spend hours (probably days actually) reverse-engineering what I download?

It take´s you about 2min to install a new kernel (depending on your hardware). And with tools like synaptic it takes you 1min to remove them (depending on your hardware). Chances are the Ubuntu mainline kernels work just fine.

If you need guidance I´ll be happy to help as soon as I am back on my Ubuntubox.

---

### Post by Only1KW on 2016-09-26
> **ian-weisser said:**
> Already suggested - Use the products of the Ubuntu Kernel Team: [https://wiki.ubuntu.com/Kernel](https://wiki.ubuntu.com/Kernel)

You're missing my point.  You're suggesting the Kernel Team's kernels because they're the most popular.  I doubt you've personally verified that their kernels are good.

---

### Post by ian-weisser on 2016-09-26
I'm suggesting the Ubuntu Kernel Team's kernels because they are _supported_.
They want your bug reports, and they respond when I file bug reports.
16.10 is currently running kernel 4.8....from the Kernel Team.

Not sure where 'personally verified' and 'spending hours reverse engineering' are coming from. I'm not seeing those in your original post.
Your original post was about suggestions for new-yet-stable kernels that you could test.
If you have other criteria, please elaborate so we don't offer you well-intentioned but useless advice.

---

### Post by Only1KW on 2016-09-27
> **Only1KW said:**
> I'd like to be able to add an apt repository to my system which contains one of these kernels so that if any new security updates come out for them, I don't have to manually track that and upgrade them.

This is what I originally asked for, and all I feel I've gotten so far in response is that it's a stupid idea.  I've been trying to justify and defend myself since then how adding a repository and using apt to install them is no worse than manually downloading them and installing using dpkg.

Edit:  On a side note, here is an example of a bug I wrote a year and a half ago: [https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/1446848](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/1446848) .  Other than some initial requests for more data and clarification, it hasn't been touched since.  I haven't bothered writing a bug since since I spent so much time meticulously collecting data for this one only to have it ignored.  And my current bug with my system crashing is historically notorious for being impossible to debug remotely as there isn't much data to even collect to indicate why the suspend failed.  I figure just trying out other kernels seeing if they work better would be faster for me, especially since I've found many other people online saying they've also had issues with power management on 4.4 and upgrading to 4.5 or newer fixed it for them.

---

### Post by ian-weisser on 2016-09-27
> **Only1KW said:**
> I've gotten so far in response is that it's a stupid idea.

I am very sorry!
We really would like to help you, not insult you.

---

