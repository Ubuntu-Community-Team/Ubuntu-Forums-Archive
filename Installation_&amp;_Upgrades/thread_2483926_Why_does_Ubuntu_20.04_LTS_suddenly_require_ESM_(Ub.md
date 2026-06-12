---
title: "Why does Ubuntu 20.04 LTS suddenly require ESM (Ubuntu Pro) to get updates?"
date: 2023-02-13
forum: Installation &amp; Upgrades
---

### Post by spattent on 2023-02-13
When I try to update all packages, I get this message:
```
$ sudo apt full-upgrade
[...]
The following security updates require Ubuntu Pro with 'esm-apps' enabled:
  mc libzmq5 mc-data
Learn more about Ubuntu Pro at https://ubuntu.com/pro

```

This is on Ubuntu 20.04 LTS:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.5 LTS
Release:        20.04
Codename:       focal

```

Why is this? As far I understand, Ubuntu 20.04 LTS was supposed to get "free" updates until 2025, and payed ESM updates would only be required after that :o
[https://ubuntu.com/about/release-cycle#ubuntu](https://ubuntu.com/about/release-cycle#ubuntu)

Why has this changed and payed ESM updates are now required even for the "LTS" versions that still *is* way _within_ its "normal" support period ?!?!

(And yes, I know that you can get "Ubuntu Pro" for free for your machines, for personal use. But I cannot use this, because this is **not **a "personal use" use case for me)

Thank you.

---

### Post by guiverc on 2023-02-13
> **spattent said:**
> When I try to update all packages, I get this message:
```
$ sudo apt full-upgrade
[...]
The following security updates require Ubuntu Pro with 'esm-apps' enabled:
  mc libzmq5 mc-data
Learn more about Ubuntu Pro at https://ubuntu.com/pro

```

This is on Ubuntu 20.04 LTS:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.5 LTS
Release:        20.04
Codename:       focal

```

Why is this? As far I understand, Ubuntu 20.04 LTS was supposed to get "free" updates until 2025, and payed ESM updates would only be required after that :o
[https://ubuntu.com/about/release-cycle#ubuntu](https://ubuntu.com/about/release-cycle#ubuntu)

Why has this changed and payed ESM updates are now required even for the "LTS" versions that still *is* way _within_ its "normal" support period ?!?!


You will continue to get the same upgrades with or without Ubuntu Pro/ESM for the five years of *standard support* for Ubuntu 20.04 LTS which ends in April 2025.

I'll provide clues as to what Ubuntu Pro provides now using one of the packages from your paste.

libzmq5, ie. [https://packages.ubuntu.com/focal/libzmq5](https://packages.ubuntu.com/focal/libzmq5)

You'll note it's a UNIVERSE package, which has never before had *security *fixes available for it, as it's a community ('universe') supported package, and security fixes applies to packages from 'main'.

If you *enable* Ubuntu Pro on 20.04 LTS, a new feature is 'security' upgrades are available for many 'universe' packages, something other distributions still do not provide even now, but are available first on Ubuntu, alas only for those using Ubuntu Pro.

If you don't enable Ubuntu PRO, there are no changes. You'll still get the same *three* years of guaranteed support as comes with packages from 'universe', though if bugs are filed and a MOTU has time available ('universe' packages are community maintained don't forget), fixes can be applied for the five years, however security options haven't altered.

Ubuntu Pro gives you an new optional facility if you deem the security benefits of it are worth enabling, ie. another choice; but no change if you opt not to enable it (*though you could also say you're nagged about new features you're opting not to use, but those messages can be disabled if you don't want to see them*)

---

### Post by MAFoElffen on 2023-02-13
I know how Ubuntu Pro works, but...

I am starting to think that the wording of this recent change in Update Messages is causing confusion and fear of what the real world is. (That they are being forced to do something.)
> 
The following security updates [COLOR=#ff0000]require[/COLOR] Ubuntu Pro with 'esm-apps' enabled:

People think, with that wording, that they have lost something, instead of gained something new, more and enhanced capabilities realized...

If they just mentioned "universe repo's" and/or enhanced coverage, this might all be different. Maybe something like:
```

If you had Ubuntu Pro with 'esm-apps' enabled, you might be getting security updates for these old versions of 'universe repo' packages:

```
LOL

---

### Post by spattent on 2023-02-13
Thanks for clarification!

And indeed, I think the wording is a bit confusing. Especially since this message appears in the LTS version while it still is ***within*** its "standard" support period.

That this applies **only **to certain *community-maintained* ("universe") packages, which _never_ were covered by the "free" long-term support anyway, is _**not**_ made clear at all :-?


IMO, the message should be:
> [FONT=lucida console]The following *optional* security updates for community-maintained ("universe") packages are available via Ubuntu Pro with 'esm-apps' enabled:
[...][/FONT]

---

### Post by grahammechanical on 2023-02-13
The problem as I see it is that the people who write messages like this and other help documentation are experts at what they do and know what they are writing about but have difficulty in looking through the eyes of someone who has no idea of what is being written about.

The presenter of a television quiz show once said: "The questions are easy if you know the answers." These people know all the answers. It is more difficult for the rest of us. We are not even given multiple choice as to what the messages could mean.

I am not complaining. Just making an observation.

Regards

---

### Post by guiverc on 2023-02-13
I'm not sure if I can add more of value to this thread, but I'll try.

I believe care was taken in trying to choose the wording, numerous people (*as I understand it*) gave input, but yes it was widely misunderstood, and it created confusion & unwanted reactions.

On Ask Ubuntu it was very busy with questions; most got *duped* to this [question]("https://askubuntu.com/questions/1452497/what-are-esm-apps-and-how-do-they-relate-to-ubuntu-pro") which I'll provide mostly for readers who might find it useful in the future.

The wording may still change (*be refined*), with one bug report [https://bugs.launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bug/1992026/](https://bugs.launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bug/1992026/)

I was I believe fully aware of all details before this, but given I've been a contributor to *Ubuntu News* since 2015, I've at least scanned if not read most if not all Ubuntu blogs & other announcements, as well as those from the Ubuntu community so have a fair understanding of where things stand.  I've seen the differences between the *official* statements about Ubuntu, and what many  *bloggers* who write about releases/announcements and probably get more readers eyes say, and I just* 'cringe*' when I read  incorrect facts [*in the 3rd party reports*].

---

### Post by BBQdave on 2023-02-14
For what it's worth Spattent, I am using Ubuntu Pro (free for up to 5 machines) to see what value there is. The free subscription has patched a few bugs involved with GNU-Image Manipulation Program (GIMP) and this is of value to me, as I use photo editing applications.

So far, no problems enabling these patches from Ubuntu Pro.

---

