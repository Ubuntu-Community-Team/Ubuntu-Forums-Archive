---
title: "installing executable file"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by sam_m on 2010-04-03
hi. am just new to linux and i have a university project so i need to install an program which is of type x-executable .when i double click over it nothing happens.
when i right click and click properties-->open with i got "no application selected"..so what is the application used to open this type of programs..any help is greatly appreciated..10x

---

### Post by CharlesA on 2010-04-03
What is the filename? There are .deb, .run and .sh files that you can execute.

---

### Post by nem75 on 2010-04-03
Hi. With Linux it's generally a better idea to install applications via the package manager (Synaptic in Ubuntu's case) than manually, especially if you're new to the OS.

A bit mor info might help. What's the name of the program, in which shape or form did it come and where did you get it?

---

### Post by sam_m on 2010-04-03
thanks for ur fast reply..the file name is pipechar it is networking tool for getting delay and available bandwidth ....etc
the original file i downloaded called ncs-linux.tgz the i unpacked it with tar xvzf...
the extracted folder called linux.i686 and inside it a folder called bin and inside bin there are several applications having a diamond shape 
here is the link [http://www-didc.lbl.gov/NCS/download/](http://www-didc.lbl.gov/NCS/download/) it is ncs-Linux.tgz.

---

### Post by CharlesA on 2010-04-03
It looks like it is a python script.

You'd run it by typing:

```
python ncsc.py
```

into a terminal.

---

### Post by sam_m on 2010-04-03
i did that ..i got a msg saying 
{Traceback (most recent call last):
    File "ncsc.py", line 10, in <module>
      import        netlogger
ImportError: no module named netlogger}
 
and btw i need to run pipechar not ncsc

---

### Post by sam_m on 2010-04-03
hi. am just new to linux and i have a university project so i need to install an program which is of type x-executable .when i double click over it nothing happens.
when i right click and click properties-->open with i got "no application selected"..so what is the application used to open this type of programs..any help is greatly appreciated..10x
i downloaded the file from [[COLOR=#444444]http://www-didc.lbl.gov/NCS/download/[/COLOR]]("http://www-didc.lbl.gov/NCS/download/")
it is ncs-linux.tgz

---

### Post by sam_m on 2010-04-03
when extracted i need the file named pipechar

---

### Post by ibuclaw on 2010-04-03
Since there is no configure/makefile, and all seem to be executables, what you would do is create a "bin" folder in your home directory, and install them there.

If you only need pipechar, then the steps I did:
```

wget http://www-didc.lbl.gov/NCS/download/ncs-Linux.tgz
tar -xf ncs-Linux.tgz

mkdir ~/bin
install linux.i686/bin/pipechar ~/bin

source ~/.profile

```

Regards
Iain

---

### Post by Chronon on 2010-04-03
Ninja'ed.  :)

---

### Post by CharlesA on 2010-04-03
Then run pipechar.

What's the problem?

---

### Post by 3rdalbum on 2010-04-03
You can run programs by dragging them to the terminal, assuming that they have execute permission.

If they don't have execute permission, then:

```
chmod +x <drag file to the terminal>
```

You can do that in the GUI as well, but it's quicker to do on the command-line.

---

### Post by Sef on 2010-04-03
Duplicate Thread; merged.

---

