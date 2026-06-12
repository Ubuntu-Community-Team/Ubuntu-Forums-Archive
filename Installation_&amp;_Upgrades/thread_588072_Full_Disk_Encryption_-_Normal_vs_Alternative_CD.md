---
title: "Full Disk Encryption - Normal vs Alternative CD?"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by TDK800 on 2007-10-23
I've read in some threads that the full disk encryption is only available in some kind of alternative install version? Is there an alternative install CD/ISO of Ubuntu 7.10 for download somewhere? If so, why isn't full disk encryption available in normal ubuntu iso? Or is the text-mode install of the normal Ubuntu 7.10 ISO meant as "alternative install"?

---

### Post by papercut on 2007-10-23
It's available here.

[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

### Post by Barnable on 2007-12-13
Can someone give me their experiences of using this full disk encryption, please.

I have looked at the screenshots on an article on softpedia but am confused as to how it would work with a laptop (which is what it's aimed at, presumably).

So, when you boot it up, it has to decrypt the whole filesystem - doesn't that impact on battery life and bootup time?

Also, what happens if your machine shuts down because the battery runs low?  There won't be enough power to run the encryption, will there, so your data remains clear.

I would really appreciate some comments on this, thanks.

---

### Post by cecil_T on 2008-01-21
I've been running full disk encryption from the alternate install CD on two laptops for a few months now (since Gutsy came out).  It works well, and I don't notice much, if any, performance degradation.   I'm sure there must be some additional CPU and maybe hard disk activity, but again it's not really noticeable on normal usage.  This is on a P4 3GHz laptop and a Core 2 Duo 2.2 GHz laptop, with just regular 2.5" internal laptop drives.

> am confused as to how it would work with a laptop
Now I'm confused - why would it be any different with a laptop?  It works fine.

Basically the only difference you see in normal usage of the machine is a small text prompt at the bottom of the screen during boot up (on the Ubuntu splash screen) where it prompts you for your encryption password.  It will wait at this screen indefinitely for you to type your password.  Once you type it and press enter, the machine continues booting as usual - the decryption is done on the fly (it doesn't decrypt the whole filesystem at once).  If you enter the decryption key incorrectly it simply returns to a blank prompt so you can type it again.

As far as battery life, again I don't think it will have much if any impact - whatever power the slightly extra CPU overhead requires.  We're probably talking less than a percent difference here.

> Also, what happens if your machine shuts down because the battery runs low? There won't be enough power to run the encryption, will there, so your data remains clear.

Again, the encryption/decryption is done on the fly as data is written/read from the hard drive, so it's never in clear text on the drive and there is no long process to wait for.  My one laptop occasionally locks up (hardware problem, memory I suspect) and I reboot it in the middle of a desktop session and it comes back up fine.

Hope that helps.

---

### Post by Sef on 2008-01-22
> I've read in some threads that the full disk encryption is only available in some kind of alternative install version?

See answers below.

>  Is there an alternative install CD/ISO of Ubuntu 7.10 for download somewhere?

Yes, there is.  Just click on the box at the bottom of the download page.

> If so, why isn't full disk encryption available in normal ubuntu iso? 

The Live CD's gui takes up a lot of space, so less space left for programs.

> Or is the text-mode install of the normal Ubuntu 7.10 ISO meant as "alternative install"?

The text-mode install is the alternate install.  It is easy to install.  The only hard part (and the same applies to the Live CD) is manually partitioning.

---

