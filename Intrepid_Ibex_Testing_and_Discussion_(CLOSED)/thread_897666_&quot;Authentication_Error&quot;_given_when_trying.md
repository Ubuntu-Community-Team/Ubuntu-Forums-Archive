---
title: "&quot;Authentication Error&quot; given when trying to log in.  Same error with safe mode, too."
date: 2008-08-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DayOldPorridge on 2008-08-22
Right now, KPPP is the only way I can connect to the internet, so in order to fix any broken packages through recovery mode, I'd need some help in trying to configure the internet connection through the command line.  I know there's a guide for doing this with wifi or ethernet, but I'm not sure how it would work with a Verizon USB modem and KPPP.

Should I simply try to fix this by chrooting into the partition with this problem?  I have no idea how to go about fixing the "Authentication Error" problem, though.  And on the extra Ubuntu partition I'd be chrooting from, I don't have KPPP installed.  So right now I'm having to use my Macbook for internet access.

Has anyone else run into this error?

---

### Post by psyke83 on 2008-08-22
[http://ubuntuforums.org/showthread.php?t=895926](http://ubuntuforums.org/showthread.php?t=895926)

---

### Post by DayOldPorridge on 2008-08-22
I must not be doing something right.  Is this what my /etc/pam.d/common-sesssion looks like:

```

#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).
#
# As of pam 1.0.1-3, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
# here's the fallback if no module succeeds
# this is obviously a completely redundant line, except that it lets us #handle better the case where there are no "Primary" modules providedsession required pam_permit.so
# prime the stack with a positive return value is there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session required                                         pam_permit.so
# and here are more per-package modules (the "Additional" block)
session required                pam_unix.so
# end of pam-auth-update config

sed -i -e'
/here.s the fallback if no modules succeeds/,/prime the stack/ {
 s/.*pam_deny.*/# this is obviously  acompletely redundant line that lets us\
# handle better the case where there are no "Primary" modules provided\
session required pam_permit.so/
 }' /etc/pam.d/common-session

```

---

### Post by DayOldPorridge on 2008-08-22
Bump.

---

