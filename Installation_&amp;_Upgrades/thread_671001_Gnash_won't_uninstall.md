---
title: "Gnash won't uninstall"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by Raivuu on 2008-01-18
Hiya im a newbie to linux and i want to uninstall gnash but ik keeps giving me errors.
First i tried it with the add/remove thingy that didn't work.
Then i tried it with the terminal and that didn't work either.
Finaly i tried it with the Synaptic package manager but that didn't work either :(

It keeps saying: 
```

dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `gnash':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Any help would be appreciated :)

---

### Post by PmDematagoda on 2008-01-18
Open the problem file in Gedit using:-
```
gedit /var/lib/dpkg/available
```
And post the first 5 lines.

---

### Post by Raivuu on 2008-01-18
Hmm 

Could not open the file /var/lib/dpkg/available using the Unicode (UTF-8) character coding.

tried using like 15 different character codings... 
Any idea which one should work? :)

---

### Post by PmDematagoda on 2008-01-18
If I am not mistaken, I think that file may be corrupted.

Open the backup of it by running:-
```
gedit /var/lib/dpkg/available-old
```

---

### Post by Raivuu on 2008-01-18
Same error as before

Could not open the file /var/lib/dpkg/available-old using the Unicode (UTF-8) character coding.


btw. thanks for the fast replies :)

---

### Post by PmDematagoda on 2008-01-18
Execute:-
```
dpkg -s gnash
```
Post the output.

---

### Post by Raivuu on 2008-01-18
Same as the first error. :(

```
dpkg-query: parse error, in file `/var/lib/dpkg/available' near line 2 package `gnash':
 value for `status' field not allowed in this context
```

---

### Post by PmDematagoda on 2008-01-18
Post the output of:-
```
ls -la /var/lib/dpkg
```

---

### Post by Raivuu on 2008-01-18
Yay it worked :)

Thanks for the fast help :)

---

### Post by davidcaiazzo on 2008-03-12
> **PmDematagoda said:**
> If I am not mistaken, I think that file may be corrupted.

Open the backup of it by running:-
```
gedit /var/lib/dpkg/available-old
```

Don't know how old this post is but ran across it. I opened up available-old did a apt-get update and everything worked perfectly. Thank you so much!

---

