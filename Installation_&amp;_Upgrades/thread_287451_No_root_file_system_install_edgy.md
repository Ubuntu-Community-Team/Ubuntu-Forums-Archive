---
title: "No root file system install edgy"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by onlybui on 2006-10-28
Hi I can't find the instructions how to fix this when installing edgy... something about editing a file and changing root pass... because im getting this error
and cant install edgy :( I cant find the file to edit... it was a python file...

---

### Post by onlybui on 2006-10-28
NEVER MIND FOUND IT

This is a known bug (40287, and others).

WARNING: Horrid kludge follows.

To install the RC (but not fix the problem) before starting the installer, edit the file /usr/lib/ubiquity/ubiquity/validation.py .

Near the end of the file, you will find the following code:

Code:

if not root: result.add(MOUNTPOINT_NOROOT)

Change this to

Code:

if not root: pass

For those not familiar with Python, the indentation is required!

This turns off the check for a root filesystem, so make damned sure that you allocate one in the installer! As I said, it is a kludge, so use at your own risk.

Regards
Alistair

they should make this a sticky

---

