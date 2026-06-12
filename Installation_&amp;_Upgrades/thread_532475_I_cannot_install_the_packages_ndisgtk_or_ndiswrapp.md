---
title: "I cannot install the packages ndisgtk or ndiswrapper!!"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by Lord Dirk on 2007-08-22
I have downloaded the two pieces (ndiswrapper and ndisgtk) on a different comp then transferred to my laptop.  Now i cannot install either of them to my laptop running ubuntu, which i need to do to get the internet on it up and running.  i have tried using the terminal commands sudo- etc in all the forums i can find, but it wont recognize the commands or it will end up starting things but then says "couldnt find any packages whose name/description matched "ndisgtk" (in this instance).  Please tell me how i can make these applications run so i can start recieving  my wireless signal again!!

---

### Post by jfinkels on 2007-08-22
> **Lord Dirk said:**
> I have downloaded the two pieces (ndiswrapper and ndisgtk) on a different comp then transferred to my laptop.  Now i cannot install either of them to my laptop running ubuntu, which i need to do to get the internet on it up and running.  i have tried using the terminal commands sudo- etc in all the forums i can find, but it wont recognize the commands or it will end up starting things but then says "couldnt find any packages whose name/description matched "ndisgtk" (in this instance).  Please tell me how i can make these applications run so i can start recieving  my wireless signal again!!

What is the exact name / file format of the files you downloaded? If they are .deb files, simply enter in the terminal:```
sudo dpkg -i *filename*.deb
```

---

### Post by Lord Dirk on 2007-08-22
I have the two files i want downloaded to the desktop- the ndisgtk setup file is "ndisgtk_0.6-0ubuntu3_all.deb", but when i put in terminal < sudo dpkg -i ndisgtk_0.6-0ubuntu3_all.deb >, it says that no such file exists! I KNOW that it is typed correctly and that the zeros are in fact zeros and not capital O's.  what am i doing wrong?!?---> Also I have fund out that i can run a package installer by right clicking on the icon and selecting install---but it still wont (this time it gives this message: Error:dependency not satifiable: ndiswrapper-utils-1.9)

---

### Post by jfinkels on 2007-08-22
> **Lord Dirk said:**
> I have the two files i want downloaded to the desktop- the ndisgtk setup file is "ndisgtk_0.6-0ubuntu3_all.deb", but when i put in terminal < sudo dpkg -i ndisgtk_0.6-0ubuntu3_all.deb >, it says that no such file exists! I KNOW that it is typed correctly and that the zeros are in fact zeros and not capital O's.  what am i doing wrong?!?---> Also I have fund out that i can run a package installer by right clicking on the icon and selecting install---but it still wont (this time it gives this message: Error:dependency not satifiable: ndiswrapper-utils-1.9)

Since I see this is your first post, I will give you an introduction on how to solve your problems, and how to help others solve your problem for you!

First thing you should do is read the first link in my signature, "Installing software".

Second thing you should do is take a look at this tutorial on navigating the filesystem using the terminal: [http://www.linuxcommand.org/lts0020.php](http://www.linuxcommand.org/lts0020.php)

Third thing you should do, is read this page: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) .

Fourth, search the forums for people who have had a similar problem (you may want to look around for a tutorial in the Tutorials & Tips section: [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100) )

Fifth, search using Google.

Now, taking a brief look at the community documentation page (the third thing on my list) shows that you might try executing these three commands in the terminal after copying the files to, for example, your home directory (you may need to read up on navigating the filesystem, using the page linked to in the second thing on my list):```

sudo dpkg -i ndiswrapper-common_*.deb
sudo dpkg -i ndiswrapper-utils*.deb
sudo dpkg -i --force-depends ndisgtk_*.deb

```

Remember, since this is an ultimately new system for you, you will have to start from the bottom and work your way up. Keep with it, and it will pay off in the end. Let me know if you need any more help after reading up.

EDIT: see here for the community documentation page on using the terminal: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

