---
title: "apache2, recreating config files"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by metalfan_ on 2010-05-11
Hi,

ive deleted /etc/apache2 and did run: 

```

sudo apt-get -o DPkg::Options::="--force-confmiss" --reinstall install apache2.2-common

```

to get the default config back.

but starting the server via:
```

sudo /etc/init.d/apache2

```

results in:
```

Syntax error on line 161 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configuration

```

line 160-163 look like this:
```

<Files ~ "^\.ht">
    Order Allow,Deny # line in question #####################
    Deny from all
</Files>

```

the funny thing is that the exact same definition is in a debian lenny server config on another server...

So why did this install a not working config?

EDIT:

i just removed apache2 via:
```

sudo aptitude remove apache2
sudo rm -r /etc/apache2

```
and reinstalled it via:
```

sudo aptitude install apache2

```
which also did not fix the config bug?

for testing i installed apache2 on another ubuntu 9.10 and did just copy the folder /etc/apache2 to my local installation - this fixed the problem.
still, why cant i reinstall apache2 with a working config?

---

### Post by ner0tic on 2010-07-06
for the sake of mention, I'm experiencing this same problem.
```
> sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  Syntax error on line 160 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configuration

```
```
> uname -a
Linux redPhoenix 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

```
```
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
#    Satisfy all
</Files>

```

---

### Post by phillw on 2010-07-06
Hi,

I've had a quick look at my conf file round about the line 160, it seems you have gained an **#** from some where.```
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>
```

Regards,

Phill.

---

### Post by ner0tic on 2010-07-06
> **phillw said:**
> Hi,

I've had a quick look at my conf file round about the line 160, it seems you have gained an **#** from some where.```
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>
```

Regards,

Phill.

this was from me trying to match my other machine's config to see if that was the issue. it was not :(

---

### Post by phillw on 2010-07-08
Hi ner0tic,

order is supplied by authz_host which should be in your mods-enabled area ```
ls /etc/apache2/mods-enabled authz_host.load
``` This should already be there. Are your apache2 installs newly installed or updated? How did you install / update them? Would you also please post the out put of ```
apache2 -v
```

Regards,

Phill.

P.S. Sorry for the delay in replying, I forgot to subscribe to this thread.

---

### Post by phillw on 2010-07-08
Hi metalfan_,

to re-install your apache2 use this method ```
sudo aptitude purge apache2-common
sudo aptitude install apache2
```

That should pull in all the config files correctly (see the above posting as to what is missing).

Regards,

Phill.
P.S. apologies for the delay - I forgot to subscribe.

---

### Post by ner0tic on 2010-07-08
> **phillw said:**
> Hi ner0tic,

order is supplied by authz_host which should be in your mods-enabled area ```
ls /etc/apache2/mods-enabled authz_host.load
``` This should already be there. Are your apache2 installs newly installed or updated? How did you install / update them? Would you also please post the out put of ```
apache2 -v
```

Regards,

Phill.

P.S. Sorry for the delay in replying, I forgot to subscribe to this thread.

```
> apache2 -v
Server version: Apache/2.2.14 (Ubuntu)
Server built:   Apr 13 2010 20:21:26

```
 my enabled dir is empty so i see my problem.  i installed via apt-get 3times doing full removes and reinstalls each time the same thing.


edit: i copied over the mods-enabeld from my other machien and made the needed links and im good to go. thanks!

---

### Post by phillw on 2010-07-08
hiyas ner0tic,

Have you tried the solution from #6, above, yet ?

Regards,

Phill.

/edit and while I was typing my message - he edited his problem :-)

---

### Post by verheek on 2011-04-04
I have the same error after uninstalling with ```
apt-get purge apache2
``` and then using locate and rm to remove anything else.  This after I had messed up my install with webmin .

Trying #6 did not fix it.  Even after the purge, all the files are still in /etc/apache2

I previously erased them and reinstalled apache2-common but still the same error.

(Ubuntu lucid all updates)

---

### Post by indubioproreo on 2011-11-04
> **metalfan_ said:**
> Hi,

ive deleted /etc/apache2 and did run: 

```

sudo apt-get -o DPkg::Options::="--force-confmiss" --reinstall install apache2.2-common

```

to get the default config back.

but starting the server via:
```

sudo /etc/init.d/apache2

```

results in:
```

Syntax error on line 161 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configuration

```

line 160-163 look like this:
```

<Files ~ "^\.ht">
    Order Allow,Deny # line in question #####################
    Deny from all
</Files>

```

the funny thing is that the exact same definition is in a debian lenny server config on another server...

So why did this install a not working config?

EDIT:

i just removed apache2 via:
```

sudo aptitude remove apache2
sudo rm -r /etc/apache2

```
and reinstalled it via:
```

sudo aptitude install apache2

```
which also did not fix the config bug?

for testing i installed apache2 on another ubuntu 9.10 and did just copy the folder /etc/apache2 to my local installation - this fixed the problem.
still, why cant i reinstall apache2 with a working config?


Hello,

the Problem about the Syntax Error on Line 160 can be fixed by linking the mods-available in mods-enabled like this:

for a in `ls /etc/apache2/mods-available/`
do
sudo ln -s /etc/apache2/mods-available/$a $a
done

I've fixed this Problem on my Ubuntu 11.10

Regards

Jürgen

---

