---
title: "Download the full warty release (main/restricted)"
date: 2004-11-24
forum: Installation &amp; Upgrades
---

### Post by s.deleeuw on 2004-11-24
Hello People,

I want to download the Warty packages from the main and restricted sections, and burn them to DVD ('s). I know it's 'better' to use the internet and configure squid to prevent unnecessary downloads, but that is not the solution I'am looking for. Those PC's are connected 28K8 .....

So I started thinking .....

I want the packages listed in:
[http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/warty-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty-updates/main/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/warty-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty-updates/restricted/binary-i386/Packages.gz)
[http://security.ubuntu.com/ubuntu/dists/warty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/warty-security/main/binary-i386/Packages.gz)
[http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/binary-i386/Packages.gz)

Generating a package-list is easy:
# zcat Packages.gz | egrep '^(Filename)(.*)(\.deb)$' | cut -d" " -f2
.....
pool/main/libg/libgksuui1.0/libgksuui1.0-dev_1.0.1-1_i386.deb
pool/main/libg/libglade/libglade-gnome0_0.17-3_i386.deb
pool/main/libg/libglade/libglade-gnome0-dev_0.17-3_i386.deb
pool/main/libg/libglade/libglade0_0.17-3_i386.deb
pool/main/libg/libglade/libglade0-dev_0.17-3_i386.deb
.....

So, when I download those packages and copy them to /var/cache/apt/archives on every PC. That would work, wouldn't it?

Just some brain-storm session, hoping for a good solution. Please add your comments on this, so I won't find myself downloading all those packages for nothing :)

Thanks in advance,
Sander

---

### Post by poptones on 2004-11-24
You'll likely want to do some filtering, or at least provide them all a common directory. This is a LOT of files and probably a couple GB just for 386. Seems like you could symlink that /var/cache folder to a share on a central machine.

It's been my experience that just putting the files there works fine. I have a couple hundred MB that I copy from machine to machine (I just keep accumulating stuff) and when I go to install a package already in the cache it finds it instantly and begins installing. 

Hmmm.. maybe burning them all to a single root folder on a DVD, then linking /var/cache to that DVD? Don't know how to make a local repository, but I do know just populating the cache works ok.

---

### Post by s.deleeuw on 2004-11-24
I've started downloading... Little more than 2000 packages, but most of them aren't too big. This is a bad idea for universe though :)

---

### Post by az on 2004-11-24
What a horribly unelegant solution!

What about using a tool made for creating debian cds?
[http://packages.debian.org/testing/admin/debian-cd](http://packages.debian.org/testing/admin/debian-cd)

Make a bunch of cds with the software you need and then do 
sudo apt-cdrom add

Or make a central repository with all the packages you want and do
dpkg-scanpackages . /dev/null > Packages
Then add the location of the Packages file (No, it does not have to be zipped)

deb file:/home/newbie/repo ./
to your sources.list

---

### Post by s.deleeuw on 2004-11-24
[QUOTE=azz]What a horribly unelegant solution!

What about using a tool made for creating debian cds?
[http://packages.debian.org/testing/admin/debian-cd](http://packages.debian.org/testing/admin/debian-cd)

Make a bunch of cds with the software you need and then do 
sudo apt-cdrom add

Or make a central repository with all the packages you want and do
dpkg-scanpackages . /dev/null > Packages
Then add the location of the Packages file (No, it does not have to be zipped)

deb file:/home/newbie/repo ./
to your sources.list[/QUOTE]
 That is a very good tip, thank you!
I moved over from Slackware a few months ago, and I still have to learn much about debian's package system. I will read some HOWTO's; I already found some links in other threads.

Thanks again
Sander

[Edit] I was asking a stupid question :) [/Edit]

---

### Post by s.deleeuw on 2004-11-25
I did some scripting to automate the download (and update) process. The next step will be to make a repository and burn it to dvd. When I figured that out, I will write an HOWTO.

Sander

[Edit] Forgot to paste 1 line of code (creating the dest. directory) [/Edit]
[Edit] Added the script as attachment [/Edit]


```
#!/bin/bash
#

RELEASES="
	http://security.ubuntu.com/ubuntu/dists/warty-security/main/binary-i386/Packages.gz
	http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/binary-i386/Packages.gz
	http://archive.ubuntu.com/ubuntu/dists/warty-updates/main/binary-i386/Packages.gz
	http://archive.ubuntu.com/ubuntu/dists/warty-updates/restricted/binary-i386/Packages.gz
	http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz
	http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-i386/Packages.gz
"

for RELEASE in $RELEASES; do

	# Download Packages.gz
	echo ""; echo "### $RELEASE"
	wget "$RELEASE" -O PACKAGES >/dev/null 2>&1

	# Extract Filename and MD5sum entries from Packages.gz
	echo -en "\E[s--- Checking ... "
	zcat PACKAGES | \
		egrep '^(Filename:\ )(.*)(\.deb)$|^(MD5sum:\ )([a-z|0-9]{32})$' | \
		cut -d" " -f2 | cut -d"/" -f2- | \
	while read FILENAME; do

		# Split Filename and read MD5sum
		FN_PATH=`dirname "$FILENAME"`
		FN_PACKAGE=`basename "$FILENAME"`
		read MD5SUM
		MD5SUM=`echo $MD5SUM | cut -d" " -f2`

		# Already downloaded ?
		echo -en "\E[1K\E8--- Checking $FN_PACKAGE ... "

		if [ ! -f "$FN_PATH/$FN_PACKAGE" ] || \
		   [ `md5sum "$FN_PATH/$FN_PACKAGE" | cut -d" " -f1` != "$MD5SUM" ]; then

			# Delete old package if MD5sum didn't match
			rm -f "$FN_PATH/$FN_PACKAGE"

			# Download package
			# (you can safely remove the --limit-rate parameter)
			echo ""; echo -n "--- Downloading $FN_PACKAGE ... "
			mkdir -p "$FN_PATH"
			wget --limit-rate 150k -O "$FN_PATH/$FN_PACKAGE" \
				"`dirname "$RELEASE"`/../../../../pool/$FILENAME" \
				>/dev/null 2>&1 || echo "Failed!"
			echo ""; echo -en "\E[s--- Checking ... "
		fi
	done

	# Clean
	rm PACKAGES

done
echo
```

---

### Post by s.deleeuw on 2004-11-25
Status update: I created a Packages.gz using dpkg-scanpackages, just like azz pointed out. Works fine from harddisk! Now burning to DVD.

---

### Post by attitude on 2004-11-26
ok, is there any cd images available?

---

### Post by s.deleeuw on 2004-11-26
[QUOTE=attitude]ok, is there any cd images available?[/QUOTE]

That is not neccesary. You can use the script to download the packages from an Ubuntu mirror. Use `dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz` to create an index file. By adding this index file to /etc/apt/sources.list you can use the downloaded packages in Synaptic. If it works, create an .iso by `mkisofs -o ../ubuntu-packages.iso -r -J .` That's all!

I will write an HOWTO for this later, but I am currently short in time.


Sander

---

### Post by attitude on 2004-11-29
The problem is that I dont have a fast connection from home, but I have a possibility to download some isos from school

---

### Post by randy on 2004-11-30
You can also mirror the apt repositories on your hard disk using debmirror.  It would replace part of your shell script.

---

