---
title: "Automate md5sum check?"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by mango42 on 2010-03-25
I have become rather enthusiastic about handing around *working* copies of Ubuntu but being fairly clueless at the command line I'm wondering whether there is a script that could automate the verification of download integrity? Preferably with a GUI where one 'just' points the script at the local *.iso then waits while the script compares the md5sum with the relevant file hashes at (eg) [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

The usual Linux 'silence at success' would be a bonus ;-)

---

### Post by zvacet on 2010-03-25
That script can be useful,but working in terminal is good too!For md5sum check there is really simple command and you can find it [here.]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by mango42 on 2010-03-26
> **zvacet said:**
> That script can be useful,but working in terminal is good too!For md5sum check there is really simple command and you can find it [here.]("https://help.ubuntu.com/community/HowToMD5SUM")

Thanks for that well known link and very helpful it is too - but there the only version of md5sum that does an automatic(?) compare appears to be, er, the windows version! :rolleyes:

I suppose basically it's down to my eyesight and a feeling that reading and comparing long hex strings 'should' be done by a software applet, not a human... ;-)

---

### Post by patchwork on 2010-03-26
This isn't perfectly automated (it requires you to copy and paste the md5sum from the website) but seems to work pretty well regardless.

```
#!/bin/bash
filename=$(zenity --file-selection --title="MD5 CheckSum For ISO images");
echo -e "\n\nPaste MD5sum from website  >>\t";
read goodsum ;
echo "Processing..."
md5sum $filename > ~/testmd5 ;
read md5 throwout < ~/testmd5;
if [ $goodsum != $md5 ]; then
  echo -e "\nError in checksum\n\nMD5sum from Input: $goodsum\nMD5sum Calculated: $md5\nType 'q' to quit" | less;
else
  echo -e "Sums match, good download\n Type 'q' to quit" | less;
fi;
rm ~/testmd5;

```Put it on your Desktop, make it executable using ```
sudo chmod +x ~/Desktop/md5.sh
``` Double-click and select "Run in Terminal"
Select your iso
Paste the md5 hash from the website, and wait for the results.


Hope this helps.

Cheers!



EDIT: For silence on success, you can simply delete these two lines ```
else
  echo -e "Sums match, good download\n Type 'q' to quit" | less;
```

Also, why I'm thinking some more on it...you can save a list of hashes to a file (in case you hand out more than just one type of cd), and select which hash to compare against.  If this interests you let me know and I'll modify the script a bit.

---

### Post by patchwork on 2010-03-26
This next version is more automated, but will require some manual setup.  

The variable 'mirror' is set to a local mirror containing the iso images and hash file you are accessing.  This only needs to be run on first-use or mirror change.  On mirror change, the old md5sum file should be removed before downloading the new file.

The hash file path must be modified to match your set-up

The list contents must be changed to match the name of the version for each hash.
For reference, I used this [mirror]("http://mirrors.rit.edu/ubuntu-releases/9.10")

It's a little clunky, but I hope it suits your needs.

```
#!/bin/bash
# Input your mirror and hash file information
mirror="http://mirrors.rit.edu/ubuntu-releases/9.10/MD5SUMS"
# Choose image to test
filename=$(zenity --file-selection --title="MD5 CheckSum For ISO images");
# Comment out next line after first download or update
wget $mirror && 
  while read goodsum version; do
    echo -e "$goodsum\t$version" >> ~/testmd5;
  done < ~/Desktop/ShellScripts/MD5SUMS ###<---- Change this directory and file to match your local setup
# This list will need to be updated when you change MD5 files
distro=$(zenity --list --title="Which Version Would You Like To Check Against?" --width=700 --height=500 --column="Version" "*ubuntu-9.10-alternate-amd64.iso" "*ubuntu-9.10-alternate-i386.iso" "*ubuntu-9.10-desktop-amd64.iso" "*ubuntu-9.10-desktop-armel+dove.img" "*ubuntu-9.10-desktop-armel+imx51.img" "*ubuntu-9.10-desktop-i386.iso" "*ubuntu-9.10-netbook-remix-i386.iso" "*ubuntu-9.10-server-amd64.iso" "*ubuntu-9.10-server-i386.iso" "*wubi.exe");
cat ~/testmd5 | grep "$distro" > ~/testresult;
read goodsum version < ~/testresult;
echo "Processing..."
md5sum $filename > ~/testmd5 ;
read md5 throwout < ~/testmd5;
if [ $goodsum != $md5 ]; then
  echo -e "\nError in checksum\n\nMD5sum from Input: $goodsum\nMD5sum Calculated: $md5\nType 'q' to quit" | less;
# Comment out next two lines for silent success
else
 echo -e "Sums match, good download\n Type 'q' to quit" | less;
fi;
rm ~/testmd5;
rm ~/testresult;

```

---

### Post by mango42 on 2010-03-27
Hi **patchwork**,

Thanks ever so much for your input - looks to be the solution. Yes, I pass around various versions of Ubuntu - mostly 8.04, 9.10 & UbuntuStudio 8.04 & 9.10. I prefer to stay one version behind the bleeding edge but Lucid Lynx is looking so very good, I just might cut myself ;-)

I'm quite pleased by how quickly Ubuntu is being adopted by complete computer illiterates in my neck of the woods and despite the many calls for help, most of these people keep coming back to tell me how Ubuntu has changed their feelings about operating systems. The overall impressions seems to be 'why on earth can't <insert other OS here> work as smoothly as this?' and  'using Ubuntu has taken the stress out of computing for me' (sic!) and 'why does Windows need 5 mouseclicks to safely remove a flash drive and Ubuntu only needs one?'

So finally, us 'clueless at the commandline' wallahs can use Linux!

---

### Post by patchwork on 2010-03-27
It's nice to see people getting the word out.  If you need any help customizing or running the scripts, let me know.  I know the scripts aren't 'professional' grade (I have only a smattering of scripting experience), but I hope you find them useful.

---

