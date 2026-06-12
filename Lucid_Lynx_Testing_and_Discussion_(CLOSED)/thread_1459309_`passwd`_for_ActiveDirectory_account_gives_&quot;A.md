---
title: "`passwd` for ActiveDirectory account gives &quot;Authentication token manipulation error&quot;"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gmoore777 on 2010-04-21
I have latest and greatest of Lucid updates.

I have ActiveDirectory integration with Samba/Winbind. (not Likewise-Open)
Logging into Console window or `ssh`-ing into machine works fine using
DOMAIN\first.last account names.

Trying to change password with the `passwd` program:

$ passwd
Changing password for DOMAIN\first.last
(current) NT password: 
passwd: Authentication token manipulation error
passwd: password unchanged
$

In the /var/log/auth.log file I get this output in conjunction with the above passwd attempt:

  pam_unix(passwd:chauthtok): user "DOMAIN\first.last" does not exist in /etc/passwd
  passwd[16109]: pam_winbind(passwd:chauthtok): getting password (0x0000002a)

  passwd[16109]: pam_winbind(passwd:chauthtok): user 'DOMAIN\first.last' granted access
  passwd[16109]: pam_unix(passwd:chauthtok): user "DOMAIN\first.last" does not exist in /etc/passwd
  passwd[16109]: pam_winbind(passwd:chauthtok): getting password (0x00000012)

I don't see anything particularly wrong with that output, other
than it seems to stop prematurely.

This is my default-created /etc/pam.d/common-password file:

password	[success=2 default=ignore]	pam_unix.so obscure sha512
password	[success=1 default=ignore]	pam_winbind.so use_authtok try_first_pass
password	requisite			pam_deny.so
password	required			pam_permit.so
password	optional	pam_gnome_keyring.so 

I've Googled for "Authentication token manipulation error", but most
cases involve local Linux accounts or other unintersting problems.

I don't think any entries in smb.conf have an effect on passwd, but here's a snippet of entries with the word "pass" or "encrypt" in them:

password server = machine.domain.com
   encrypt passwords = true
   passdb backend = tdbsam
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   encrypt passwords = true


I can successfully change password, using `passwd` for a local Linux account.

$ passwd
Changing password for localAccount.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
$

---

### Post by dino99 on 2010-04-21
reconfigure winbind or remove/purge then reinstall, 
you can use gconf editor too
i suppose you own the rights to do that and are not hacking :)

---

### Post by gmoore777 on 2010-04-26
I built out a new machine with LucidLynx ReleaseCandidate.
(which should be the same as purging and re-installing any package).
I have the same problem with `passwd`.

Were you certain that purging and reinstalling winbind would
resolve the issue?

Do you have ActiveDirectory integration(Samba/Winbind) on your machine and `passwd` works for your ActiveDirectory account names?

---

### Post by gmoore777 on 2010-04-27
I just logged a bug against Samba/Winbind:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/570944](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/570944)

---

### Post by gmoore777 on 2010-04-29
Question:

Does anyone have `passwd` working for an ActiveDirectory account on HardyHeron using winbind (not Likewise-open) 
or
does anyone have `passwd` working for an ActiveDirectory account on 
LucidLynx using Likewise-open
or
does anyone have `passwd` working for an ActiveDirectory account on 
LucidLynx using just winbind (not Likewise-open)?

Please respond.

(Note: i am not interested in `passwd` working for local linux accounts
nor interested in `passwd` working for HardyHeron using Likewise-open)

---

