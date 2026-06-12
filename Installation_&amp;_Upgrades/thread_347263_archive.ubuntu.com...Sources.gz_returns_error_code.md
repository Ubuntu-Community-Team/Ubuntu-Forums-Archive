---
title: "archive.ubuntu.com...Sources.gz returns error code (1)"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by Phrawm48 on 2007-01-27
Although multiple Synaptic repositories are working properly, one repository has returned exactly the same error code for three days, as follows:

http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:[/url] Sub-process gzip returned an error code (1)

I can, however, use a Web browser to go to this URL:

[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)

This address produces a length listing of packages and related information.

I used Synaptic to look at the repositories but can't isolate the specific problem.

Can someone please suggest a remedy?

Cheers & thanks,
Ric
SFO

---

### Post by taurus on 2007-01-27
Edit your /etc/apt/sources.list and remove the **us** in front of that repo, [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/).

```
gksudo gedit /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Phrawm48 on 2007-01-28
Thanks, it seems to have worked.

I say "seems" because now Synaptic's "Downloading Package Information" status display peremptorily closes itself when it thinks it's finished updating the repositories.  So I can't check if the error occurs or not...

If you have any ideas what I broke, please let me know.  Otherwise I'll limp along until I stumble upon the reason the behavior of the Downloading display changed...

Cheers & thanks 'gain,
Ric
SFO

---

### Post by taurus on 2007-01-28
Can you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```
Othewise, try

```
gksudo synaptic
```

---

### Post by Phrawm48 on 2007-01-28
Hi:

I can and did run the first two "sudo apt-get" commands after editing sources.list as directed.  The original error code 1 no longer appears.  (And now that I know about them, those two commands are really handy...)

I can also run the gdksudo synaptic command.  But now, and regardless of how I start the Synaptic GUI, after clicking Reload the update window peremptorily closes after reloading of listed repositories has completed.

I can't imagine how modifying sources.list or running any of the CLI commands would change the behavior of the Synaptic GUI.  It must be a coincidence...

Cheers, thanks 'gain, & take care,
Ric
SFO

---

