---
title: "Installing Folding@Home"
date: 2013-04-16
forum: Installation &amp; Upgrades
---

### Post by U2D2 on 2013-04-16
To begin with, I am a total beginner who basically just learned that "sudo" has the same effect as "Please" in kindergarten, so i really have less than no idea of what I am doing. 

With that being said, I have been trying to install Folding@Home for about two days, and i feel that my craziness-sense REALLY has started tingeling. The thing is that I manage to get the thing down and under my feet once, I created an account(i think) and got the settings in order, but as I left OpenBox, my server started dropping all my beautiful work. Could someone please direct me somewhere or instruct me through it? I Own an about 4 year bladeserver of 10 blades with quite a lot of power, and i would really like to contribute to this fantastic project.

Thank you in advance

-Rasmus

---

### Post by U2D2 on 2013-04-16
As I mentioned, I am trying to install it to one of the servers, just to make it clear

---

### Post by Cheesemill on 2013-04-16
Installing and configuring F@H just takes a couple of commands.

First of all we need to download the F@H client installation files...
```
wget https://fah.stanford.edu/file-releases/public/release/fahclient/debian-testing-64bit/v7.3/fahclient_7.3.6_amd64.deb
```
The wget command downloads files from the internet, we're using it to download the Ubuntu F@H client from their website.

Once the download has completed we just need to tell Ubuntu to install the package...
```
sudo dpkg -i fahclient_7.3.6_amd64.deb
```

The installer will prompt you for a username, team number, passkey, system utilization profile and autostart settings.
You can safely just keep hitting ENTER to accept the default choices and you'll be up and folding straight away. If you have an existing username or team you can just enter your values instead of accepting the defaults. You don't need to register a username if you want to use one, just use it as your 'username' value.

The team number is only used if you want your users progress to count in team standings, if you're just in it for the science then this isn't required.
Some people enjoy having team or user bragging rights (try and get yourself in the top 100 folders), whereas some teams will reward you for participation.

A passkey is used to tie a particular member to a username. Because there is no restriction on people choosing user names then obviously there are going to be more than one user trying to use the same unique name. Having a passkey ensures that your points are only going to affect ***your*** standings rather than everyone that uses your username.

The system utilization profile configures how much of your machines power is going to be used for folding, it ranges from as little as possible to as much as possible.

The auto-start setting is self-explanatory. Do you want your F@H client to automatically start when the system boots?

Once you have the client running on your blades, you can use the [FAHcontrol]("http://https://fah.stanford.edu/file-releases/public/release/fahcontrol/debian-testing-64bit/v7.3/fahcontrol_7.3.6-1_all.deb") software on another machine to keep track of the progress/logs of all of your clients.

---

### Post by U2D2 on 2013-04-17
Thanks alot mate, i will do give it a try as soon as i get the beast going tomorrow!
Got another of those beginner-questions though is there a way of copypasting commands into the therminal? Done all of the typing manualy, and as english isnt my mother-languish, that is a bit time-consuming

---

### Post by Cheesemill on 2013-04-17
If you are working directly on the keyboard and monitor plugged into your server then you can't really cut and paste.

What the majority of people do when running a server is to install openssh-server (this can even be done as part of the installation process on the tasksel screen) and then just use the ssh command from a terminal on your workstation to connect to it for administration purposes.
If you do this then you can just copy/paste directly from the web browser into your terminal application.

---

### Post by U2D2 on 2013-04-19
I made it! All seem to be installed and ready and all, but I do not know if it is working or not, is there any easy interface that I can find for the FAH? Because I really don't know if it is working or not. 4-5 new processes are active, but I have no idea of how to see which once

I'm reading up on the OpenSSH now, but I think that I will do that tomorrow though, seems a bit complicated for a Friday-brain^^

---

### Post by U2D2 on 2013-04-19
I found out by reading a bit closer on the install-thingy #-o thank you so very much mate, I am more than grateful for your patient and unconditional help, people like you warms my heart

---

