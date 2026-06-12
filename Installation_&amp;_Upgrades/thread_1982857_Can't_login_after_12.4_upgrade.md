---
title: "Can't login after 12.4 upgrade"
date: 2012-05-19
forum: Installation &amp; Upgrades
---

### Post by troudobus on 2012-05-19
Hi,

 Yesterday I upgraded from 11.4 to 11.10 and it went fine.
Then I upgraded from 11.10 to 12.4 and it's not fine. :(
I can't login my session (though it's possible as Guest). I tried deleting the .Xauthority file, I read it solved the problem for some, but with no effect.
I noticed:
 - The session manager (not sure of its name: the screen where you choose your account) displays "ubuntu 11.10"
 - There are some broken dependencies in the package manager (there wasn't before the upgrade).
 - I tried to resolve them using  *apt-get upgrade --full-resolver* and *apt-get -f install.* For the later it stopped on an error from dpkg due to some lexmark package
 - Which I tried to purge, but is still there and to forbid *apt-get -f install* to succeed.
 - In the .xsession-errors I read the first error is "the control display is undefined" => how can I define one?

Any help or suggestion would be great.
Thanks


PS: I used xfce as desktop manager and awesome as window manager.

---

### Post by sikander3786 on 2012-05-19
Can you please post the error that you encountered while trying to execute 'apt-get -f install'?

Even if you can't, I am sure that there are some broken packages on your PC. Probably, not all of the packages were upgraded while the upgrade process was running because of the same error you mentioned.

So, you might need to get rid of that error and try upgrading again with:

```
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get dist-upgrade
```

---

### Post by troudobus on 2012-05-19
Thank you Sikander,

 That's more or less what I've tried to do.* (EDIT: though I didn't know in which order)*
When I execute sudo apt-get install -f I get:

"
dpkg: error: parsing file '/var/lib/dpkg/status' near line 6495 package 'lexmark-inkjet-09-driver':
  blank line in value or field 'Description'
E: Sub-process /usr/bin/dpkg returned an error code (2)
"

---

### Post by sikander3786 on 2012-05-19
Ok. There is a problem with your dpkg status file. Try using the old one instead:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

And try the above mentioned commands again.

---

### Post by troudobus on 2012-05-19
Yes! 
Actually both in /var/lib/dpkg/status and in /var/lib/dpkg/available there was a blank line I filled with a "." (seems dpkg parses blank lines as a separation between two packages declaration and in the case of this lexmark package there was such accidental blank line, instead of a simple dot to create a separation for the human reader).
And then dist-upgrade finished the work.

Thank you very much!

---

