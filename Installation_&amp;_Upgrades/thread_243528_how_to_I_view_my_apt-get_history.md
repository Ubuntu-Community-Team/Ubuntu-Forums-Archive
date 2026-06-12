---
title: "how to I view my apt-get history?"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by cantormath on 2006-08-25
Does anyone know how to view the apt-get installation history, ie, the packages I installed and the dependencies that were install as apart of things I installed? Thanx....

---

### Post by wjp.reg on 2006-08-25
> **cantormath said:**
> Does anyone know how to view the apt-get installation history, ie, the packages I installed and the dependencies that were install as apart of things I installed? Thanx....

Have you checked ```
/var/log/aptitude
```for the info you're looking for?

---

### Post by benteveo on 2006-10-01
Users who don't use aptitude don't have */var/log/aptitude*

My system seem to have this alternative:

```
$ grep install /var/log/dpkg.log
```

but it only shows the installation log since the last rotation (last day or so).  There are also 2 rotated files dating back about 2 months (dpkg.log.1 and dpkg.log.2.gz). I wish there was a bigger history configured in logrotate by default. I feel installation history is too important to lose.

---

### Post by ThunderouS on 2007-11-09
*seems to be outdated but just for the record*
apt-get keeps a very clean log on file
*/var/log/apt/term.log*
*sudo cat /var/log/apt/term.log *
will do the job

---

### Post by 1337455 10534 on 2007-11-10
I had found one of these files earlier but it had a complete list of every single thing I  have typed into the terminal, ever. I'd like to find that list please..

---

### Post by bobbarry on 2007-12-18
> **ThunderouS said:**
> *seems to be outdated but just for the record*
apt-get keeps a very clean log on file
*/var/log/apt/term.log*
*sudo cat /var/log/apt/term.log *
will do the job

I'm using Gutsy, and I routinely use apt-get.  I only rarely use dpkg, and never aptitude, to install packages.  But there is no /var/log/apt/term.log on my system.  Can you suggest why?  Is there a way to retrieve it or turn it on?

---

### Post by zvacet on 2007-12-18
You can find it in** synaptic>file>history**.

---

### Post by phatchow on 2008-01-31
Here is what I think the original poster was getting at, and surprisingly does not have a simple solution.  Let's say 3 months ago on a different machine I install 50 packages with 300 dependencies (possibly not realistic, but whatever).  Now, I want a record of what I've done so I can reproduce my results later.  

All the solutions suggested so far do not distinguish between the "top-level" packages and the dependencies.  I could reproduce the results by re-installing everything and letting apt complain when re-install attempts are made, but there should be a more elegant solution.

---

### Post by handydan918 on 2008-05-13
I know this thread is ancient, but for those stumbling here via google:


```
dpkg --get-selections>some_stupid_filename.txt
```

And to use it to select and install packages, do 

```
dpkg --set-selections<some_stupid_filename.txt
apt-get dselect-upgrade
```

---

### Post by _Stevie_ on 2008-05-25
i only use aptitude (apart from external packages, then i have to use
dpkg). is the /var/log/aptitude complete or does it get truncated when
it reaches a certain size?

---

### Post by chochem on 2008-05-26
Although the solution proposed by hardydan918 doesn't meet the need phatchow points out, it's still probably the best mentioned in this thread. Even if you do not intend to use it to reproduce the exact installation, it's perfectly useable as the list is human readable and 100% complete (meaning including whatever packages the install process has installed).

---

