---
title: "Unable to update core20"
date: 2023-08-19
forum: Installation &amp; Upgrades
---

### Post by daanheuvelbeuk on 2023-08-19
I get a regular update request for "update core20". I always perform updates, as it should keep my system safe. But this update fails each time:
[IMG]https://i.postimg.cc/J4PDRgns/Screenshot-from-2023-08-19-10-11-35.png[/IMG]


When looking at my system configuration I see I am running "22.04.3 LTS (Jammy Jellyfish)". So is my snap confused, or am I lagging?

[IMG]https://i.postimg.cc/q77NtGN1/Screenshot-from-2023-08-19-10-14-34.png[/IMG]

---

### Post by ian-weisser on 2023-08-19
Everything you need should be in the output of

```
snap info core20
```

If you need further help interpreting the output, post it.

---

### Post by MAFoElffen on 2023-08-19
If you are having issues with a Snap, especially for the core/foundation Snap app's, there is a way to force a reinstall of Snap core20... (Without having to remove/install.)
```

sudo snap refresh core20 --channel=edge
sudo snap refresh core20 --channel=stable

```

---

### Post by grahammechanical on 2023-08-19
This is my guess as to what is happening. It is based upon my observations.

When Ubuntu loads the OS checks for updates in the background. Ubuntu software registers that updates are available. Ubuntu Software can be used to do updates. Meanwhile, we run Software Updater which automatically updates any snap apps. But Ubuntu Software does not know about this. It still registers snap updates available. So, when we tell Ubuntu Software to update the snap apps it cannot find any updates because they have already been installed and the channel is now empty.

Regards

---

### Post by daanheuvelbeuk on 2023-08-20
> **ian-weisser said:**
> Everything you need should be in the output of

```
snap info core20
```

If you need further help interpreting the output, post it.

```
$ snap info core20
name:      core20
summary:   Runtime environment based on Ubuntu 20.04
publisher: Canonical&#10003;
store-url: https://snapcraft.io/core20
contact:   https://github.com/snapcore/core20/issues
license:   unset
description: |
  The base snap based on the Ubuntu 20.04 release.
type:         base
snap-id:      DLqre5XGLbDqg9jPtiAhRRjDuPVa5X1q
tracking:     latest/stable
refresh-date: yesterday at 10:10 CEST
channels:
  latest/stable:    20230801 2023-08-18 (2015) 66MB -
  latest/candidate: 20230801 2023-08-10 (2015) 66MB -
  latest/beta:      20230801 2023-08-02 (2015) 66MB -
  latest/edge:      20230803 2023-08-03 (2027) 66MB -
installed:          20230801            (2015) 66MB base

```

---

### Post by ian-weisser on 2023-08-20
> **daanheuvelbeuk said:**
> ```

latest/stable:    20230801 2023-08-18 (2015) 66MB -
[...]
installed:          20230801            (2015) 66MB base

```

There you have it. You are running the latest stable.

Next time you get a prompt to check core20, check that same command's output.

If you are running the latest, then no further action is needed; the prompt was stale (as @grahammechanical suggested)
If you are not running the latest, then a simple 'sudo snap refresh` should put you onto the latest. Or no action at all, as snapd updates four times completely automatically every day already.

If you get repeated prompts, that means that the software is in use, and must be Quit before the refresh can occur.

---

### Post by grahammechanical on 2023-08-20
By the way, on my Ubuntu 20.04.3 the snap packages are as up to date as the snap packages on the OP's operating system. Even though 20.04 is two years earlier than 22.04. It is a benefit of snap packaging.

> graham@graham-Hybris:~$ snap info core20
name:      core20
summary:   Runtime environment based on Ubuntu 20.04
publisher: Canonical&#10003;
store-url: [https://snapcraft.io/core20](https://snapcraft.io/core20)
contact:   [https://github.com/snapcore/core20/issues](https://github.com/snapcore/core20/issues)
license:   unset
description: |
  The base snap based on the Ubuntu 20.04 release.
type:         base
snap-id:      DLqre5XGLbDqg9jPtiAhRRjDuPVa5X1q
tracking:     latest/stable
refresh-date: 3 days ago, at 00:14 BST
channels:
  latest/stable:    20230801 2023-08-18 (2015) 66MB -
  latest/candidate: 20230801 2023-08-10 (2015) 66MB -
  latest/beta:      20230801 2023-08-02 (2015) 66MB -
  latest/edge:      20230803 2023-08-03 (2027) 66MB -
installed:          20230801            (2015) 66MB base

Regards

---

