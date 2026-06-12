---
title: "Fresh Install of Edgy LAMP: pam_foreground.so undefined symbol"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by plincoln on 2006-12-07
Hello all,

Ive been a long time debian user, and decided to give Ubuntu a whirl for my server needs. Installed LAMP Edgy last nite, and noticed in the syslog:

authdaemond: PAM unable to dlopen(/lib/security/pam_foreground.so)
authdaemond: PAM [dlerror: /lib/security/pam_foreground.so: undefined symbol: pam_set_data]
authdaemond: PAM adding faulty module: /lib/security/pam_foreground.so

I checked to make sure the module is there, and it is. The only reference to pam_foreground.so is in /etc/pam.d/common-session:


# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).  The default is pam_unix.
#
session required        pam_unix.so
session        optional        pam_foreground.so

I am not sure what's causing the error, but for the time being I have commented it out without adverse affects. Any insight is appreciated.

Thanks
patrick

edit:

Here is the ldd output 

@boon:/lib/security$ ldd -r pam_foreground.so
undefined symbol: ioctl (./pam_foreground.so)
undefined symbol: malloc        (./pam_foreground.so)
undefined symbol: pam_set_data  (./pam_foreground.so)
undefined symbol: unlink        (./pam_foreground.so)
undefined symbol: sprintf       (./pam_foreground.so)
undefined symbol: __xstat       (./pam_foreground.so)
undefined symbol: __errno_location      (./pam_foreground.so)
undefined symbol: pam_get_data  (./pam_foreground.so)
undefined symbol: pam_get_user  (./pam_foreground.so)
undefined symbol: open  (./pam_foreground.so)
undefined symbol: mkdir (./pam_foreground.so)
undefined symbol: close (./pam_foreground.so)
undefined symbol: free  (./pam_foreground.so)
        statically linked

---

### Post by martinfst on 2006-12-12
I encountered the same problem on an 6.10 server install. I could not get courier to authenticate correctly, so I had to fix it. I installed ONLY ubuntu 6.10 packages. No compiling from source.

I did notice the version of pam_foreground.so on 6.10 was compiled by one of the ubuntu members (Daniel Silverstone) - See Readme in /usr/share/doc. It looks like it has been compiled/linked against a different library. Would be nice if this could be properly fixed on a regular 6.10 update.

For the time being I used the suggestion to comment the optional line in /etc/pam.d/common-session

Martin

---

### Post by eric_stewart on 2007-03-01
Thanks for the information.  I googled for this issue and found this posting.  I, too, commented out the line and I'm not getting annoyed by that silly message anymore.

I'm using Courier-MTA 0.53.3 with IMAP / ESMTP / POP3 modules.

/Eric

---

### Post by matthewmceachen on 2007-03-08
I just opened [https://launchpad.net/ubuntu/+source/libpam-foreground/+bug/90720](https://launchpad.net/ubuntu/+source/libpam-foreground/+bug/90720) with a reference to this thread.

---

### Post by djamu on 2007-09-19
got a patched deb file for those who need it ( i386 )

usage : sudo dpkg -i libpam-foreground_0.3_i386-patched.deb

greetz

---

