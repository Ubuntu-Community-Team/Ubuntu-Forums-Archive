---
title: "Notice appears while upgrading 20.04 to 22.04.1"
date: 2022-08-20
forum: Installation &amp; Upgrades
---

### Post by astronomertom on 2022-08-20
Just before choosing to install this upgrade, a notice popped up reporting things like
# of packages no longer supported by Canonical
# of packages being removed
etc.

I couldn't find a way to cut-n-paste this report to save it, since this might have info important for configuring all my other software after the upgrade.

Is this information saved anywhere?  Perhaps with some metadata of why it is being removed (replaced with newer revision, etc.)?

For that matter, is there a general 'upgrade log' stashed anywhere it can be checked?

Thanks
Tom

---

### Post by ActionParsnip on 2022-08-20
Copy the text then you can make a pastebin if you like.

---

### Post by astronomertom on 2022-08-20
> **ActionParsnip said:**
> Copy the text then you can make a pastebin if you like.

You couldn't even select the text.

Copy would only be possible transcribing by hand.  There are 100+ entries.

---

### Post by SeijiSensei on 2022-08-21
If this is running in a terminal, you almost certainly should be able to copy the text by highlighting it with your mouse and right-clicking to choose Copy.

Another option is to route all the output to a file:
```
sudo apt full-upgrade > /path/to/some/file 2>&1
```
The "2>&1" part redirects any errors sent to stderr (output 2) to stdout (1) and sends it to the file as well.

---

### Post by astronomertom on 2022-08-22
> **SeijiSensei said:**
> If this is running in a terminal, you almost certainly should be able to copy the text by highlighting it with your mouse and right-clicking to choose Copy.

Another option is to route all the output to a file:
```
sudo apt full-upgrade > /path/to/some/file 2>&1
```
The "2>&1" part redirects any errors sent to stderr (output 2) to stdout (1) and sends it to the file as well.

So that is a distinction between using the terminal vs. the GUI in upgrading.  Guess I'll have to remember that for 24.04.

Thanks,
Tom

---

### Post by ActionParsnip on 2022-08-23
> **SeijiSensei said:**
> If this is running in a terminal, you almost certainly should be able to copy the text by highlighting it with your mouse and right-clicking to choose Copy.

Another option is to route all the output to a file:
```
sudo apt full-upgrade > /path/to/some/file 2>&1
```
The "2>&1" part redirects any errors sent to stderr (output 2) to stdout (1) and sends it to the file as well.

Could even pipe to pastebinit rather than a file. It'll make the URL for you in the terminal

---

