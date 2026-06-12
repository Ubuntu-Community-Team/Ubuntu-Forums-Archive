---
title: "It appears that installing OpenLDAP broke SSH"
date: 2019-05-04
forum: Installation &amp; Upgrades
---

### Post by thekirkwoods on 2019-05-04
I've been searching for a week and can't seem to find a solution. So, I need your help.

I am using Ubuntu 18.10.

Basically, I've installed OpenLDAP (I'm still really new at it, so it's just in a test phase), and within the LDAP server are two usernames, 'john' and 'test'.

I can 'su john' just fine, all works as expected. In fact, I believe (and I'll check again) that I can even 'su matt', which is a name which was added directly to the Ubuntu OS as a standard user.

However, I can't SSH to any user, even if that user is in the LDAP server or just in the OS. When I attempt to SSH, the process hangs for a moment, and eventually says 'Incorrect Password'. This is causing other additional problems that I need to solve.

Anyways, I could just post a bunch of config files and settings, or I could just start from scratch and open the forum for a conversation. Please question me and ask to see copies of various files, screenshots or whatever, and I'll post them to facilitate the troubleshooting process. In return, please let me know if there is a specific area of detail I may have overlooked.

Thanks again!

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Update May 5, 2019
When I installed OpenLDAP, I did the following actions:
[LIST=1]
[*]installed slapd and ldap-utils
[*]dpkg-reconfigure slapd
[*]ldapadd -x -D cn=admin,dc=practice,dc=net -W -f add_entries.ldif
[/LIST]

When I installed the ldap client, I did the following actions:
[LIST=1]
[*]installed libnss-ldap, libpam-ldap, and ldap-utils
[*]sudo auth-client-config -t nss -p lac_ldap
[*]sudo pam-auth-update
[*]sudo gedit /etc/pam.d/common-session
[/LIST]

I have attached a screenshot of my common-session file as well as a couple other screenshots.

Any advice that you all can add, would be greatly appreciated!

Thank you!

---

### Post by TheFu on 2019-05-04
Installing openldap doesn't put the posix schema that is required for Unix logins. I don't know if it modifies the PAM files either.  Last time I setup servers to use LDAP, all of that was manual configuration.  I think there were around 10 steps to get a client authenticating to an LDAP server.

18.10 isn't LTS, so I won't touch it, especially on a server.  18.04 ... 20.04 are my next planned Ubuntu Installs. We're on 16.04 still and not in a hurry.

---

### Post by thekirkwoods on 2019-05-05
Thanks for replying.  I have the LDAP server and client working, sort of.  I have another issue which I 'think' is a second issue, not related to this one.  Basically, I can 'su' to the new user, but I can't seem to log into the Ubuntu OS using the new LDAP user.  However, my first and most critical problem is that I have lost the ability to SSH.

If there's any chance that you have a different (better?) how-to guide on how to install an LDAP server and client, even on an older version of Ubuntu, I'd be very appreciative to have a copy.

Thanks again for your reply.

---

### Post by TheFu on 2019-05-05
Did you update the sshd in /etc/pam.d/ to use LDAP?
Also, 
[https://wiki.debian.org/LDAP/PAM](https://wiki.debian.org/LDAP/PAM) says:> 
If using OpenSSH, you may need to add "UsePAM yes" to sshd_config or it will not use PAM by default. 

BTW, using *sudo gedit* isn't safe. It may have broken your ~/.config/ directories.  Always use **sudoedit** to edit system files, except those with specific tools, like visudo.

---

### Post by thekirkwoods on 2019-05-05
Yes, I have "UsePAM yes" set in my /etc/ssh/sshd_config file.  I came across that too at one point, but determined it didn't aid in my solution.  See the screenshot attached.

---

### Post by thekirkwoods on 2019-05-05
Also, I attempted to do SSH using -vvv and received the output contained in the attached text file.

---

