---
title: "how to install"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by hakopjs on 2008-05-03
Hi, I just downloaded a linux based java application and I dont know what to do with, or how to install it, I am new to linux and dont really know how to install programs after downloading it, please help me step by step, anyone.  Thanks

---

### Post by atomkarinca on 2008-05-03
Can you tell what the application is or what is the filetype of the file you downloaded? (e.g. tar.gz, deb, bin etc.)

---

### Post by hakopjs on 2008-05-03
yes its a bin file

---

### Post by atomkarinca on 2008-05-03
> **hakopjs said:**
> yes its a bin file

Then the steps you should follow should most probably be like this:

1. Open up a terminal: Applications > Accessories > Terminal (Sorry I just realized you're using kubuntu. Hit alt+f2 and type konsole)
2. Browse to the directory where you saved the .bin file:

```
cd /home/your_username/directory_you_saved_the_file
```

3. Then you should make the file executable:

```
chmod +x filename.bin
```

4. Finally you should run the .bin file:

```
./filename.bin
```

---

### Post by hakopjs on 2008-05-03
do i use the same codes to extract any bin file?

---

### Post by atomkarinca on 2008-05-03
These are the steps to run .bin files. Although there should be a mini-guide how to install that file on the page you downloaded the file.

---

### Post by hakopjs on 2008-05-03
Do you agree to the above license terms? [yes or no]
           yes
Unpacking...
Checksumming...
Extracting...
./jre-6u5-linux-i586-rpm.bin: 370: ./install.sfx.7721: not found


what does this mean

---

### Post by hakopjs on 2008-05-03
does this mean it was installed?

---

### Post by atomkarinca on 2008-05-03
If you're trying to install java then this should be a lot easier:

```
sudo apt-get install sun-jre6-jre
```

But if you want to install it with the .bin file then I guess you downloaded the wrong binary file. You should download "[Linux self extracting binary file]("Linux self extracting binary file")" and follow the same steps.

---

### Post by hakopjs on 2008-05-03
thank you sooo much, I appreciate your help

---

### Post by atomkarinca on 2008-05-03
No problem. Welcome to the community :)

---

