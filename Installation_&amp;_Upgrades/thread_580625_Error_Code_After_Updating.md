---
title: "Error Code After Updating"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Zeenomorph on 2007-10-18
I updated my system in preparation for Gutsy.  There were no problems during the updates, but when I hit 'check' when it was done, I got this message;

W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7

Any ideas?

---

### Post by Zeenomorph on 2007-10-18
Another question.... I was going to start to download the Gutsy, but I was thwarted by this question;

What type of computer do you have?

Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM) 
or
64bit AMD and Intel computers

Aren't Pentium, and Intel the same company?  How do I know which to choose?  I have an Asus F5V notebook.  They use the term 'Intel' on their sight.  Is that what I should go with?

---

### Post by DrewBoo on 2007-10-18
> **Zeenomorph said:**
> Another question.... I was going to start to download the Gutsy, but I was thwarted by this question;

What type of computer do you have?

Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM) 
or
64bit AMD and Intel computers

Aren't Pentium, and Intel the same company?  How do I know which to choose?  I have an Asus F5V notebook.  They use the term 'Intel' on their sight.  Is that what I should go with?

I think you're just reading it wrong.  Or perhaps it wasn't phrased ideally.

You're choosing between an *Intel Pentium computer* or an *Intel 64bit computer*.

Intel is the company.  Pentium is one of their 32 bit products.


Your Asus laptop shipped with an *Intel Core 2 Duo* processor.  Double-check your laptop and look for that branding.

That processor can handle both 32bit and 64bit binaries.  Search these forums to weigh the pros and cons of each of those two flavors.

---

### Post by Zeenomorph on 2007-10-19
How do I know which one I have?

---

### Post by DrewBoo on 2007-10-19
> **Zeenomorph said:**
> How do I know which one I have?

See my edit above.

Happy installing.

---

### Post by webbie180 on 2007-10-19
> **Zeenomorph said:**
> I updated my system in preparation for Gutsy.  There were no problems during the updates, but when I hit 'check' when it was done, I got this message;

W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7

Any ideas?

Same thing happen to me too, any help??

---

### Post by DrewBoo on 2007-10-19
> **webbie180 said:**
> Same thing happen to me too, any help??

Judging from that address...do you remember installing or using software called "screenlets"?

Do you use it, or were you just trying it out once?

---

### Post by Zeenomorph on 2007-10-24
I just tried it once.  I didn't like it, I thought that it was uninstalled.

---

### Post by DrewBoo on 2007-10-24
> **Zeenomorph said:**
> I just tried it once.  I didn't like it, I thought that it was uninstalled.

I suspect you did uninstall it.  The error you're getting implies that it's the *install* that went a little messy.

It sounds like you've told your machine to look for screenlets updates, but you never got the signature key for screenlets updates.  And this is all made irrelevant since you're not even interested in screenlets.

I will instruct you on removing the screenlets updates.  This should be pasted into the terminal.

First, make a copy of the update sources, to be safe.
[INDENT]```
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.screenlets
```[/INDENT]

Now, edit the sources.  Remove the entire line that contains "http://hendrik.kaju.pri.ee".  I suspect that it will be a single line, near the bottom of the file.
[INDENT]```
 sudo gedit /etc/apt/sources.list
```[/INDENT]

Now when you check for updates there should be no complaints.  Let me know how it goes.

---

### Post by Zeenomorph on 2007-10-24
That was awesome.  It worked like a charm.  Thank you very much!

---

