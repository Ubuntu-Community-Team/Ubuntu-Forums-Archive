---
title: "Problems with /etc/apt/sources.list.d"
date: 2015-09-15
forum: Installation &amp; Upgrades
---

### Post by juanuni on 2015-09-15
When I make ```
apt-get update
``` returns ```
Ignorando archivo «canonical_partner.list’» en directorio «/etc/apt/sources.list.d/» dado que tiene una extensión de nombre de archivo inválida

``` this can be translate like [SIZE=4]**"**[/SIZE] [FONT=comic sans ms]Ignoring file "canonical_partner.list '' in '/etc/apt/sources.list.d/' directory as it has an invalid filename extension [/FONT][SIZE=4]**"**[/SIZE]. [COLOR=#ff0000]How fix this? [/COLOR][COLOR=#000000]&#8203;. Sorry for my English.[/COLOR]

---

### Post by deadflowr on 2015-09-15
Does the entry really show as canonical_partner.list' ? (notice the ' symbol at the end)
If so you might simply use something like move(mv)
I'd change directories first
```
cd /etc/apt/sources.list.d
```
perhaps a quick ls (That's LS, but in small letters) to see the entries beforehand to double check.
then
```
sudo mv canonical_partner.list' canonical_partner.list
```
this should fix the messed up extension.

Hope it helps.

---

### Post by ajgreeny on 2015-09-15
I note the information about you and your distro says you are using **Distro:    Ubuntu 10.04 Lucid Lynx**

Can you confirm that is no longer the case as 10.04 is now out of support.

---

### Post by juanuni on 2015-09-15
> **ajgreeny said:**
> I note the information about you and your distro says you are using **Distro:    Ubuntu 10.04 Lucid Lynx**

Can you confirm that is no longer the case as 10.04 is now out of support.
Sorry. I have my info outdated. I'm on Ubuntu minimal 14.04.

---

### Post by juanuni on 2015-09-15
> **deadflowr said:**
> Does the entry really show as canonical_partner.list' ? (notice the ' symbol at the end)
If so you might simply use something like move(mv)
I'd change directories first
```
cd /etc/apt/sources.list.d
```
perhaps a quick ls (That's LS, but in small letters) to see the entries beforehand to double check.
then
```
sudo mv canonical_partner.list' canonical_partner.list
```
this should fix the messed up extension.

Hope it helps.
No works

---

### Post by Bashing-om on 2015-09-15
juanuni; Hello;

Perhaps we can spot the problem. Post back - between code tags - the output of terminal command:
```

cat /etc/apt/sources.list.d/*.list

```

an extra set of eyes ->
[INDENT][INDENT][INDENT]never did hurt a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by deadflowr on 2015-09-15
> **juanuni said:**
> No works

Oops, you need to encapsulate it
try
```
sudo mv "canonical_partner.list'" canonical_partner.list
```

---

### Post by juanuni on 2015-09-16
> **deadflowr said:**
> Oops, you need to encapsulate it
try
```
sudo mv "canonical_partner.list'" canonical_partner.list
```

Ocurrs this:
```
sudo mv "canonical_partner.list'" canonical_partner.list
mv: no se puede efectuar `stat' sobre «canonical_partner.list'»: No existe el archivo o el directorio
```
but the file exists.

PD:. [COLOR=#ff0000]constantly I must relogin to response. Is very frustrating. [/COLOR]

---

### Post by QIII on 2015-09-16
juanuni --

Hello!

I'm sorry about the fact that you have to log back in.  Unfortunately, we can do nothing about that.  Canonical IS has put a timeout on logins.  None of us here works for Canonical, but they host the servers.  I assure you that this has been brought to their attention, but we can do nothing further.

Thanks for understanding.

---

### Post by juanuni on 2015-09-16
> **Bashing-om said:**
> juanuni; Hello;

Perhaps we can spot the problem. Post back - between code tags - the output of terminal command:
```

cat /etc/apt/sources.list.d/*.list

```

an extra set of eyes ->[INDENT][INDENT][INDENT]never did hurt a thing
[/INDENT]
[/INDENT]
[/INDENT]

the server forces me to relogin. Just works with fast responses like this.

---

### Post by juanuni on 2015-09-16
> **juanuni said:**
> the server forces me to relogin. Just works with fast responses like this. I cant write all output because the server forces me to relogin. >:(

---

### Post by QIII on 2015-09-16
If I am not mistaken, you should have two hours before you have to log in again.  Again, sorry.  We can't change that.

---

### Post by juanuni on 2015-09-18
> **QIII said:**
> juanuni --

Hello!

I'm sorry about the fact that you have to log back in.  Unfortunately, we can do nothing about that.  Canonical IS has put a timeout on logins.  None of us here works for Canonical, but they host the servers.  I assure you that this has been brought to their attention, but we can do nothing further.

Thanks for understanding.
No problem. I understand. :(

---

### Post by juanuni on 2015-09-18
> **QIII said:**
> If I am not mistaken, you should have two hours before you have to log in again.  Again, sorry.  We can't change that.
No, only a few minutes.

---

