---
title: "How do you install tar.bz2 packages?"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by Th3Blaze on 2010-08-23
Please can you tell me how to install tar.bz2 packages.

Thanks In Advance

---

### Post by v0idloser on 2010-08-23
You can't literally "install" them.

A .tar.bz2 file simply means a tar archive which is compressed using the bzip2 compression method.

You're probably referring to a source which is packaged that way.

Unpack the file using the following command:

For safety concerns, first move the file to another directory.
We'll call this directory "build".

```
mkdir build
mv tarfile.tar.bz2 build
cd build
tar xvf tarfile.tar.bz2

```

A bunch of files and directories will be unpacked into the build directory.

Read the README or INSTALL file in the build directory and follow the instructions there.

---

### Post by Th3Blaze on 2010-08-23
mkdir build
th3blaze@janus:~$ mv tarfile.tar.bz2 build
mv: cannot stat `tarfile.tar.bz2': No such file or directory
th3blaze@janus:~$ cd build
th3blaze@janus:~/build$ tar xvf dolphin-2.0.amd64.tar.bz2
tar: dolphin-2.0.amd64.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
th3blaze@janus:~/build$ mkdir build
th3blaze@janus:~/build$ mv dolphin-2.0.amd64.tar.bz2 build
mv: cannot stat `dolphin-2.0.amd64.tar.bz2': No such file or directory
th3blaze@janus:~/build$ cd build
th3blaze@janus:~/build/build$ tar xvf dolphin-2.0.amd64.tar.bz2
tar: dolphin-2.0.amd64.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
th3blaze@janus:~/build/build$ mkdir build
th3blaze@janus:~/build/build$ mv dolphin-2.0.amd64.tar.bz2 build
mv: cannot stat `dolphin-2.0.amd64.tar.bz2': No such file or directory
th3blaze@janus:~/build/build$ cd build
th3blaze@janus:~/build/build/build$ tar xvf dolphin-2.0.amd64.tar.bz2
tar: dolphin-2.0.amd64.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


That's the terminal's
output

---

### Post by v0idloser on 2010-08-23
Your problem was that you tried to copy the literal file "tarfile.tar.bz2".

Your tar file is actually called dolphin-2.0.amd64.tar.bz2.

Lets repeat the process.

Open the terminal.

```
rm -r build

mkdir build

mv dolphin-2.0.amd64.tar.bz2 build

cd build

tar xvf dolphin-2.0.amd64.tar.bz2
```

Try this.

---

### Post by Th3Blaze on 2010-08-23
th3blaze@janus:~$ rm -r build
th3blaze@janus:~$ 
th3blaze@janus:~$ mkdir build
th3blaze@janus:~$ 
th3blaze@janus:~$ mv dolphin-2.0.amd64.tar.bz2 build
mv: cannot stat `dolphin-2.0.amd64.tar.bz2': No such file or directory
th3blaze@janus:~$ 
th3blaze@janus:~$ cd build
th3blaze@janus:~/build$ 
th3blaze@janus:~/build$ tar xvf dolphin-2.0.amd64.tar.bz2
tar: dolphin-2.0.amd64.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
th3blaze@janus:~/build$

---

### Post by brad_c6 on 2010-08-23
ok, first we need to extract the file out of the .tar.bz2.

First check if file-roller is installed (Allows you to make/extract archives graphically).

```
sudo apt-get install file-roller
```

Second, double click the archive on whereever you have it saved(In your case "dolphin-2.0.amd64.tar.bz2")

Third, click "extract" in the top center toolbar, and choose where you want to extract the file. (I will say Desktop, by clicking Desktop then extract)

Forth, we got the files out of the archive and now open that folder and there are the files.


To run the program "dolphin-emu" there are certain package(s) you need to ensure you have by running

```
sudo apt-get install libportaudio0
```


Now tha we got that double click "dolphin-emu" and your ready to go!

---

### Post by v0idloser on 2010-08-23
Alright.

Where is dolphin-2.0.amd64.tar.bz2 located?

In your terminal, under your home directory:

```
ls | grep dolphin
```

How did you download the file? Did you use a web browser to download it? If so, it may be in some directory where the browser saves everything it downloads. Go to that directory and see if it's there.

---

### Post by Th3Blaze on 2010-08-23
th3blaze@janus:~$ /home/th3blaze ls | grep dolphin
bash: /home/th3blaze: is a directory
th3blaze@janus:~$ ^C

I did the libaudio0 thing and it did whatever it was supposed to do.

I clicked on the dolphin emu thing and it didn't work.

The tar.bz2 is in /home/th3blaze/downloads

and the binary folder that was in it is in /home/th3blaze/documents/Wii Emulator

---

### Post by brad_c6 on 2010-08-23
Run this
```
cd /home/th3blaze/documents/Wii Emulator/Binary/Linux-x86_64
```

then this

```
./dolphin-emu
```

What error comes out?

---

### Post by Th3Blaze on 2010-08-23
th3blaze@janus:~$ ls | grep dolphin
th3blaze@janus:~$ /home/th3blaze ls | grep dolphin
bash: /home/th3blaze: is a directory
th3blaze@janus:~$ ^C
th3blaze@janus:~$ cd /home/th3blaze/documents/Wii Emulator/Binary/Linux-x86_64
bash: cd: /home/th3blaze/documents/Wii: No such file or directory
th3blaze@janus:~$ ./dolphin-emu
bash: ./dolphin-emu: No such file or directory
th3blaze@janus:~$ ./dolphin-emu

I forgot to say thanks 4 everythin so far!

---

### Post by brad_c6 on 2010-08-23
No Problem, always willing to help out...

ok how about this drag the "dolphin-emu" file into the terminal, what appears?

(What we are looking for is the "location" or path of the file on your computer)

---

### Post by Th3Blaze on 2010-08-23
It just shows where the file i slocated

---

### Post by brad_c6 on 2010-08-23
Right because in terminal you want to inside that folder and then run

```
./dolphin-emu
```

To start Dolphin

---

### Post by Th3Blaze on 2010-08-23
?
What do you mean?

---

### Post by Th3Blaze on 2010-08-23
brad????
What on Earth do u mean?
It doesn't make sense

---

### Post by brad_c6 on 2010-08-23
Copy and paste and then enter for each of the following into the terminal

```
sudo add-apt-repository ppa:glennric/dolphin-emu
```
```
sudo apt-get update
```
```
sudo apt-get install dolphin-emu
```

then to run it type
```
dolphin-emu
```

or go to Applications--->Games--->Dolphin Emu

---

### Post by Th3Blaze on 2010-08-23
dolphin-emu: command not found


th3blaze@janus:~$ sudo add-apt-repository ppa:glennric/dolphin-emu
[sudo] password for th3blaze: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv CBA82405A9D3DADD0A6647D16C843CCE8505D44B
gpg: requesting key 8505D44B from hkp server keyserver.ubuntu.com
gpg: key 8505D44B: public key "Launchpad PPA for glennric" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
th3blaze@janus:~$ dolphin-emu
dolphin-emu: command not found
th3blaze@janus:~$ ./ dolphin-emu
bash: ./: is a directory
th3blaze@janus:~$ ./dolphin-emu
bash: ./dolphin-emu: No such file or directory
th3blaze@janus:~$ sudo dolphin-emu
sudo: dolphin-emu: command not found
th3blaze@janus:~$ dolphin-emu
dolphin-emu: command not found
th3blaze@janus:~$ 


th3blaze@janus:~$ sudo add-apt-repository ppa:glennric/dolphin-emu
[sudo] password for th3blaze: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv CBA82405A9D3DADD0A6647D16C843CCE8505D44B
gpg: requesting key 8505D44B from hkp server keyserver.ubuntu.com
gpg: key 8505D44B: "Launchpad PPA for glennric" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

---

### Post by Th3Blaze on 2010-08-23
i THINK IT WORKS THANKS!

---

### Post by brad_c6 on 2010-08-23
Now run (This updates Ubuntu's package list)
```
sudo apt-get update
```

then run (This is where Ubuntu installs Dolphin)
```
sudo apt-get install dolphin-emu
```

then run (This will run the game, this last step you can instead click Applications--->Games----->Dolphin Emu)
```
dolphin-emu
```

---

### Post by brad_c6 on 2010-08-23
No Problem have fun! :D

---

