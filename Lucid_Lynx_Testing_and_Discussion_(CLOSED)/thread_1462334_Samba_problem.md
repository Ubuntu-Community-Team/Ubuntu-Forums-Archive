---
title: "Samba problem"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by whitetimer on 2010-04-25
Hi All

I am running xubuntu lucid RC and have Samba etc installed, but when i try /etc/init.d/samba restart i get sudo: /etc/init.d/samba: command not found

How do i sort this out please ?

Many Thanks

:KS

---

### Post by MacUntu on 2010-04-25
Isn't it 'smbd' instead of 'samba' (and as that is already an upstart job in /etc/init it should be 'sudo restart smbd')?

---

### Post by whitetimer on 2010-04-25
> **MacUntu said:**
> Isn't it 'smbd' instead of 'samba' (and as that is already an upstart job in /etc/init it should be 'sudo restart smbd')?


Right ok ... When i do that, this is the reply 

> 
sudo restart smbd
smbd start/running, process 2088



---

### Post by EMCGFX on 2010-04-26
You can also add this in your /home/USER/.bashrc file or .bash_aliases. This is small function I wrote, nothing special but will let you turn off or on the samba.

To turn it off type:
samba stop

To turn it on type:
samba start

You can also add restart and other if you like.

```
## Samba Function
samba() {
  case $1 in
    stop) ## Stop Samba
      sudo stop smbd ;;
    start) ## Start Samba
      sudo start smbd ;;
    *) echo 'Error' ;;
  esac
}

```

---

### Post by Lampi on 2010-04-26
What about the advertising daemon (nmbd)? Is it necessary to restart it too if I made changes to smb.conf?

---

### Post by EMCGFX on 2010-04-26
> **Lampi said:**
> What about the advertising daemon (nmbd)? Is it necessary to restart it too if I made changes to smb.conf?

nmbd — NetBIOS name server to provide NetBIOS over IP naming services to clients

So no. You don't need to restart it.

---

