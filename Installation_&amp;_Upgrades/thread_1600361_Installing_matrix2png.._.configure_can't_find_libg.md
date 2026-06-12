---
title: "Installing matrix2png.. ./configure can't find libgd"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by superdan111 on 2010-10-18
Hi all, almost total newbie here. Slowly getting the hang of it. So, in a burst of enthusiasm, I decided to 
1) Learn a new operating system
2) Learn a new programming language
3) assemble the entire genome of an organism on a desktop computer

So far getting my *** kicked.

I am installing a program called SolexaQA which tells you how good your genome sequencing run was (bio-geek talk, don't worry about it).

It requires dependent programs, one of which is matrix2png. matrix2png in turn is dependent on GD, or libgd. I thought I had installed libdg with

```
sudo apt-get install php5-gd
```seems to work ok.

so then go to the directory where matrix2png is

```
cd /home/<user>/matrix2png-1.2
```then

```
./configure
```and configure starts, does its thing, then says 

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for sin in -lm... yes
checking for main in -lpng... yes
checking for main in -lz... yes
checking for gdImageCreate in -lgd... no
configure: error: You need to have libgd installed and findable by the configure script
See `config.log' for more details.
```so what am I doing wrong? Is GD and libgd the same thing? is libgd installed and I just have to tell configure how to find it? am I doing something fundamentally wrong?

remember almost total newbie here

Thanks:guitar:

---

### Post by superdan111 on 2010-10-18
woops..SOLVED sorry, just needed to properly install the dependent program using sudo

---

### Post by Mucku_Mucku on 2010-10-19
Nice... so you also stumbled over the SolexaQA release...

I can't get it compiled even with "php5-gd" installed.

What did you exactly do?

Cheers,

Markus

---

### Post by Mucku_Mucku on 2010-10-19
Me again,

By the way FastQC is also a nice and similar program... but the output doesn't look so sexy though...

[http://www.bioinformatics.bbsrc.ac.uk/projects/fastqc/](http://www.bioinformatics.bbsrc.ac.uk/projects/fastqc/)

---

### Post by superdan111 on 2010-10-27
yes it was a nightmare for a newbie.

Basically download GD from [http://www.libgd.org/releases/](http://www.libgd.org/releases/)
unzip the package (I used [gd-2.0.35.tar.bz2]("http://www.libgd.org/releases/gd-2.0.35.tar.bz2") but I'm not sure it matters)
produces a folder called gd-2...etc
navigate to the folder in the terminal
then, when you are in the gd-2-0-35 folder in the terminal (I am not sure you need to use "sudo" for all of these but I did)

sudo ./configure
sudo make
sudo make install

then install matrix2png... 
same as before, download from
[http://www.bioinformatics.ubc.ca/matrix2png/](http://www.bioinformatics.ubc.ca/matrix2png/)

I think it's the same, unzip, then put the unzipped folder somewhere, then navigate to the appropriate folder in the terminal, then

./configure
make
make install

(put sudo before the command if it does not work due to a lack of admin privileges)

If it doesn't give you the error message about libgd, you are in business

then to install R which is a statistical package also required for SolexaQA
in the terminal:

sudo apt-get install r-base-core

then, run solexaQA:
navigate to wherever SolexaQA.pl is in the terminal
then:
perl SolexaQA.pl (name of the input file, including the full path) (then any variables, look in the SolexaQA readme/manual)
the output files will turn up in the same folder as SolexaQA.pl, takes quite a while!

any probs reply and I'll do my best to help, I know how frustrating it can be
:guitar:

---

