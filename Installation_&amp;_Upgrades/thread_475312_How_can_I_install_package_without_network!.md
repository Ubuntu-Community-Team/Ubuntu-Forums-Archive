---
title: "How can I install package without network!"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by riverstore on 2007-06-15
My computer doesn't connect to network, how can I install package, such as alien.
Thanks.

---

### Post by smartboyathome on 2007-06-16
You have to have a network connection to install packages. Ubuntu is just that way. ;)

---

### Post by Daisybobs on 2007-06-16
If the program you want shows up in synaptic when you search, this should work fine.

Run Synaptic, and go to the File menu. In there you will find 'Generate package download script'. So, select all the packages you want to install and generate the script.

Take that script to a linux computer connected to the internet (I will explain windows way too). Put the script in a new folder because it will download lots of files.  Remove the script file after you've downloaded everything.

Once you've got the files back to your computer, go to the file menu in synaptic again.  In there is a option called 'Add downloaded packages'. Click that and open the folder which contains the deb files. Remember, it will complain if you have anything other than the deb files in that folder!

For Windows.
Generate the script as per usual. Open the script in gedit, click on 'Replace' Icon. Enter these:
**In the search for box:**
wget -c
**In the replace with box:**
<a href="

Click the Replace All button. Repeat the replace with these two:
**Search for:**
.deb
**Replace with:**
.deb" >Package link</a><br>

**Replace the first line with this text:**

<html><head></head><body>

**And add this line to the bottom**
</body></html>

Now you can save that file as a .html file and use it in windows.

---

### Post by riverstore on 2007-06-19
Thank for help, I've follow your instruction but Synaptic just generate this:
[COLOR="Blue"]#! /bin/sh[/COLOR]
In my country, most of people use Windows, I've just used Ubuntu  for a month, I get  many problem. :sad:
(Sorry for my English ;))

---

### Post by tomislav on 2007-07-02
Hi,

I've tried doing as you said but I can't find the package I want in synaptico. More precisely, I'm looking for Bluefish but from the looks of it the numbero of available packages in my synaptico is not even a shadow of the actual number that are available on the internet.

Can you please help me?

---

### Post by derby007 on 2007-07-02
Visit : [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") then download your desired packages, ie. .deb files & dependencies, copy these .deb files onto YOUR system (without Internet connection), 'right-click' and install using gdebi program.

---

### Post by tomislav on 2007-07-02
You don't understand, I don't want to do that because I'd need to install 30 dependancies for Bluefish alone. I've been asking for help for that matter and been told to read this thread and use the technique shown by Daisybobs. However, Daisybobs doesn't say what should I do if I don't find the package I need in synaptic.

Again, my synaptic seems to have 10 times less programs and packages than the packaged.ubuntu.com website.

---

### Post by riverstore on 2007-07-23
> **derby007 said:**
> Visit : [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") then download your desired packages, ie. .deb files & dependencies, copy these .deb files onto YOUR system (without Internet connection), 'right-click' and install using gdebi program.

This is all I need. Thank you very much!

---

