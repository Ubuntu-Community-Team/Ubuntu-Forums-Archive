---
title: "Unable to install tar.gz file"
date: 2015-07-24
forum: MINT
---

### Post by pranish on 2015-07-24
I wanted to install a program so i downloaded its tar.gz format. I used the following command

```
tar -xzf archive-name.tar.gz
cd archive-name
./configuremake
sudo make install

```
but when I run ./configure command, it gave me the following error

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gconftool-2... /usr/bin/gconftool-2
checking whether NLS is requested... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: in `/home/viper/Downloads/gwget-1.0.2':
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

---

### Post by papibe on 2015-07-24
Hi pranish.

What did you download? 

From where (link)?

Where are the instructions you were trying to follow (link)?

The last line says:
```
See `config.log' for more details.
```
Could you paste the content of the log, or if it is too long paste it here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/) and post back the link to the pasted text?

Regards.

---

### Post by SeijiSensei on 2015-07-24
Did you run
```
sudo apt-get install build-essential
```
before trying to compile?  You do have a copy of gcc, but maybe you're missing some other vital components?

---

### Post by oldos2er on 2015-07-24
Moved to MINT.

Gwget looks like it hasn't been updated in a long time, just FYI.

---

