---
title: "Cannot cancel sudo password request with a single Ctrl-C"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-04-16
Pretty weird: I cannot abort a sudo password request (gnome-terminal and VT) with a single Ctrl-C key combo. Instead the request is shown again and if I push Ctrl-C again or use the enter key I'm back to the prompt:

```
test@box:~$ sudo echo "foo"
[sudo] password for test: *[COLOR="Red"]// Ctrl-C[/COLOR]*
[sudo] password for test: *[COLOR="Red"]// Ctrl-C or Enter[/COLOR]*
test@box:~$ 
```

I can reproduce this with a second machine I've used during the Lucid dev cycle but I can't with a daily live CD (changed sudoers to ask for a pwd), so maybe some upgrade-voodoo has jinxed my machines. :-k

Any ideas where I should dig to find the root of all evil? It's definitely not the sudo package.

---

### Post by MacUntu on 2010-04-16
FWIF, directly sending SIGINT to the sudo process has the same effect.

Am I really alone with this?

---

### Post by coffeecat on 2010-04-16
> **MacUntu said:**
> 
Am I really alone with this?

No. I can confirm the same here. Haven't a clue why though.

---

### Post by cariboo on 2010-04-16
When I try to run your command, copy and pasted from the post, I get:

```
sudo echo "Oachkatzlschwoaf!"
bash: !": event not found
```

---

### Post by Bachstelze on 2010-04-16
> **cariboo907 said:**
> When I try to run your command, copy and pasted from the post, I get:

```
sudo echo "Oachkatzlschwoaf!"
bash: !": event not found
```

This was obviously a bogus command...

---

### Post by MacUntu on 2010-04-16
Oooops, sorry!

**Edit:**

So, after a bit of thinking I found something in _/etc/pam.d/common-auth_:

Weird behavior:
```
auth	[success=2 default=ignore]	pam_unix.so nullok_secure
auth	[success=1 default=ignore]	pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
auth	requisite			pam_deny.so
auth	required			pam_permit.so
```

Expected behavior:
```
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
auth	requisite			pam_deny.so
auth	required			pam_permit.so

```

---

### Post by MacUntu on 2010-04-16
Ok, this is caused by installing winbind, will open a bug report.

Bug report: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/564842](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/564842)

---

