---
title: "CUPS PDF Print Problem"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by mainak_sen on 2010-07-26
I have been using Hardy for last 2 years and there were no problems and I used the print to PDF (by selecting PDF as my default printer) option very often. Ever since I upgraded to Lucid last week this is not working any longer. Even the "Print Test Page" option is not working. The various error messages I am getting are given below.
Interestingly, I have upgraded to Lucid in another machine and there also I am getting the same errors.

I shall greatly appreciate if someone could help us!

Thanks in advance!

----Error Messages-----

Print Error: There was a problem printing document 'Test Page' (job 76: 'Stopping job because the scheduler could not execute the backend.'

Stopped - Printer Configuration error

Status Messages: There is a missing print filter for printer 'PDF

---

### Post by cside on 2010-09-15
I had a similar problem, and I found that at some point Cups-PDF became uninstalled. I reselected the package, possibly just remark it for installation in Synaptic and see if this resolves your problem. Once mine was installed it all work.

---

### Post by jaygo on 2010-10-20
It seems obvious now but I didn't think to check if that package was still installed; for some reason, the upgrade to 10.10 went out of its way to uninstall cups-pdf. Thanks!

---

### Post by neiljansons on 2010-10-25
cups-pdf printing was working fine with 10.04 but the upgrade to 10.10 trashed it.
I have tried uninstalling & reinstalling with no joy
any ideas?

---

### Post by Bucky Ball on 2010-11-08
Same prob. I have cups-pdf installed and no different. Prints test page, PDF takes forever (30 minutes?) and the result is a garbled mess.

Anyone had any success? I'm using 10.10.

ps: My understanding was cups-pdf is an app. for printing a text file to a pdf file *rather than* a printer, not printing a pdf file to a printer.

---

### Post by crazybilly on 2010-11-18
Apparently, this was a bug in Cairo, the underlying graphics layer that Evince uses.

[https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/661724](https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/661724)

According to the bug report, it looks like the fix rolled out in a recent update (which I can't yet confirm, as I'm installing the update now).

---

### Post by Bucky Ball on 2010-11-21
I swapped to acroread and prints no problem. :)

---

### Post by neiljansons on 2010-11-21
This thread seems to have strayed. The problem described was with Cups-Pdf printing (ie. printing to a .pdf file).
Since I upgraded to 10.10 this no longer works even though I have uninstalled and reinstalled several times.

---

### Post by lmarmisa on 2010-11-21
The installation of cups-pdf is not perfect. This program tries to write the PDF files in the folder **~/PDF**, but this folder has to be created manually by the user. If the directory is not created

```

mkdir ~/PDF

```cups-pdf does not work.

I do not know if this can be the cause of your problem.

Check if the folder PDF exists and check the contents of the config files

[B]/etc/cups/cups-pdf.conf
[/B]
```

...
###########################################################################
#                                      #
# Path Settings                                  #
#                                      #
###########################################################################

### Key: Out
##  CUPS-PDF output directory 
##  special qualifiers: 
##     ${HOME} will be expanded to the user's home directory
##     ${USER} will be expanded to the user name
##  in case it is an NFS export make sure it is exported without
##  root_squash! 
### Default: /var/spool/cups-pdf/${USER}

**Out ${HOME}/PDF**
...

```and **/etc/apparmor.d/usr.sbin.cupsd**

```

...
# separate profile since this needs to write into /home
/usr/lib/cups/backend/cups-pdf {
  #include <abstractions/base>
  #include <abstractions/fonts>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  capability chown,
  capability fowner,
  capability fsetid,
  capability setgid,
  capability setuid,

  # unfortunate, but required for when $HOME is 700
  capability dac_override,

  /bin/dash ixr,
  /bin/bash ixr,
  /bin/cp ixr,
  /etc/papersize r,
  /etc/cups/cups-pdf.conf r,
 [B] @{HOME}/PDF/ rw,
  @{HOME}/PDF/* rw,[/B]
  /usr/bin/gs ixr,
  /usr/lib/cups/backend/cups-pdf mr,
  /usr/lib/ghostscript/** mr,
  /usr/share/** r,
  /var/log/cups/cups-pdf_log w,
  /var/spool/cups-pdf/** rw,
}
...

```I prefer to use the Desktop folder as destination for the PDF files. So, I changed the string **PDF** to **Desktop** in the two config files and it works great.

---

### Post by neiljansons on 2010-11-22
Thanks lmarmisa for attempting to help
I had already redirected the output of cups-pdf to a directory that existed but I actually like your idea of sending it to the desktop. I have now changed it to that.

However it is still not working.

BTW the location of usr.sbin.cupsd is /etc/cups/apparmor.d/ not /etc/apparmor.d/

---

### Post by lmarmisa on 2010-11-22
> **neiljansons said:**
> BTW the location of usr.sbin.cupsd is /etc/cups/apparmor.d/ not /etc/apparmor.d/

Thanks for you comment but the mistake was in the path of the file /etc/cups/cups-pdf.conf. I have fixed it in my post.

---

