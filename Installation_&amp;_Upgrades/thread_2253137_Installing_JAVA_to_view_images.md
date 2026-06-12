---
title: "Installing JAVA to view images"
date: 2014-11-17
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2014-11-17
How do I install JAVA?  I need to install this to view images

---

### Post by slickymaster on 2014-11-17
You can install it via a PPA ((Personal Package Archive) and thus getting every update through your update manager.

Open a terminal window and run the following commands```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

---

### Post by sofasurfer on 2014-11-22
My mistake,I am sure I have Java. What I need is Java Runtime.
I want to display an image but I am told I need to install Java Runtime Environment. When I try to install the plugin I am told that it is not available. It also offers me the opportunity to install it manually. When I click manual install I am taken to a Firefox website that talks about Java. Sorry to say that I find it quite confusing. 
I am sure I have Java but how can I check? If I have Java doesn't that mean I also have Java Runtime?

I tried to install "Default JRE" in synaptic but I got a message, "Cannot apply changes. Fix broken packages first". It does not tell me what packages are broken. 

What to do?

---

### Post by flaymond on 2014-11-22
Can you tell us what kind of image do you wanna view? Is it images on your Browser or on your Desktop? Is it like JPEG picture or runtime images? 


If its on your browser, you can enable JavaScript

---

### Post by Elfy on 2014-11-22
> **sofasurfer said:**
> ...

I tried to install "Default JRE" in synaptic but I got a message, "Cannot apply changes. Fix broken packages first". It does not tell me what packages are broken. 

What to do?

In synaptic - check custom filter - broken is in there.

---

### Post by sofasurfer on 2014-11-22
> **InterProg said:**
> Can you tell us what kind of image do you wanna view? Is it images on your Browser or on your Desktop? Is it like JPEG picture or runtime images? 


If its on your browser, you can enable JavaScript



This is the image. It is a platt map on a local government website.
[http://www.dleg.state.mi.us/platmaps/dt_image.asp?BCC_SUBINDEX=12292](http://www.dleg.state.mi.us/platmaps/dt_image.asp?BCC_SUBINDEX=12292)

---

### Post by sofasurfer on 2014-11-22
> **Elfy said:**
> In synaptic - check custom filter - broken is in there.

It shows that the broken dependency is "default JRE". What command do I use to repair it?

---

### Post by slickymaster on 2014-11-24
> **sofasurfer said:**
> My mistake,I am sure I have Java. What I need is Java Runtime.
If you have Java installed then you have Java Runtime Environment (JRE)
> **sofasurfer said:**
> I want to display an image but I am told I need to install Java Runtime Environment. When I try to install the plugin I am told that it is not available. It also offers me the opportunity to install it manually. When I click manual install I am taken to a Firefox website that talks about Java. Sorry to say that I find it quite confusing. 
I am sure I have Java but how can I check? If I have Java doesn't that mean I also have Java Runtime?
To check if Java is installed run the following command in a terminal window:```
java –version
```or test it at the [Sun Java test webpage]("http://www.java.com/en/download/help/testvm.xml").

To enable Java in Firefox, in a terminal window do the following:```
sudo -i
mkdir -p /usr/lib/mozilla/plugins
```
Then go to Fierfox plugins directory before you make the symbolic link.```
cd /usr/lib/mozilla/plugins
```and create the symbolic link:```
ln -s /usr/local/java/jre1.7.0/lib/amd64/libnpjp2.so ## replace jre1.7.0 with your installed jre version
```Restart your browser.

---

