---
title: "Intrepid Ibex fingerprint scanner"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bufke on 2008-10-05
Hello

I'm using intrepid beta.  I the fingerprint scanner works, but when setting it up in /etc/pam.d/common-auth I'm not sure what to do.  My file looks like this

```

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-5, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```

This is different than what [https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger) says, so I assume then that Intrepid changed the pam-auth file.  I tried replacing it they way the wiki says so, but the results in a half working fingerprint and the ability to access root by canceling gksudo.  Can any one help?

---

### Post by midnightflash on 2008-10-07
I'm just stuck at the same... still trying.

---

### Post by t.alex on 2008-10-09
same issue here. i can't seem to get it work right.

//by the way, shouldn't this thread be moved to Development & Programming ?

---

### Post by e04mk on 2008-10-19
I've been trying different pam-configurations as well but I can't get it to work appropriately. I'm not sure wheter it's a problem with pam talking to thinkfinger, or if it's just configurating pam correctly. Does anyone have any idea?

---

### Post by Timon&amp;Pumba on 2008-10-19
I used to have my "common-auth" config file like below.
It worked fine up to a week ago, when I decided not to use it anymore, so I assume this configuration is still correct:

First it tries your fingerprint device, and if it fails it falls back to password login.

Good luck!
Timon

```

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#

# fingerprint device
auth	sufficient	pam_fprint.so

auth	sufficient	pam_unix.so try_first_pass nullok_secure
auth	optional	pam_smbpass.so migrate missingok

```

---

### Post by miguelfm on 2008-10-19
Right now, there is a problem which force us to do carrier return after passing the finger. I have seen the bug report some minutes ago. I hope it'll be solved before the release date :). 

> **Timon&Pumba said:**
> I used to have my "common-auth" config file like below.
It worked fine up to a week ago, when I decided not to use it anymore, so I assume this configuration is still correct:

First it tries your fingerprint device, and if it fails it falls back to password login.

Good luck!
Timon

```

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#

# fingerprint device
auth	sufficient	pam_fprint.so

auth	sufficient	pam_unix.so try_first_pass nullok_secure
auth	optional	pam_smbpass.so migrate missingok

```

---

### Post by frigaut on 2008-10-24
It also works for me, nstalling the required packages and following the instructions on [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger) : 

$ sudo apt-get install thinkfinger-tools libpam-thinkfinger

$ sudo /usr/lib/pam-thinkfinger/pam-thinkfinger-enable

and then acquiring and verifying (see link above)

but I confirm the fact that one has to do a carriage return after swapping ones fingerprint. I'm running the latest ibex as of oct 24.

---

### Post by Neffscape on 2008-10-29
Same problem here with Intrepid RC1 installed yesterday (two days before the final release). So in the end what we have to do with this thinkfinger thing? 

btw, thinkfinger is the only package out there to enable fingerprint reading and login in GNU/Linux? Is there nothing easier to use and configure?

---

### Post by frigaut on 2008-10-29
Regarding the extra carriage return, there is a bug report and a proposed work around (which worked for me) at
[https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429](https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429)

---

