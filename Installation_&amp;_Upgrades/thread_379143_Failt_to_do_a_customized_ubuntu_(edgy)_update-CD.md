---
title: "Failt to do a customized ubuntu (edgy) update-CD"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by Philipp99 on 2007-03-08
I try to do an Software-Update CD for TuxLab OS. But I fail to do so ...

I have installed Tuxlab (which is based on EduBuntu 6.10) from the DVD and have added some addistional packages from diverent DVDs (3 Universum DVDs and orginal Ubunutu 6.10 DVD). 
For the installation I used synaptic.

My aim is now, to compile, based on the actual installation an Update CD, which contains the addistional-installed packages (including his dependances) on it. Finaly on the CD will be an Updates.gz repository.

I already know how to compile a custom repository and to add it to sources.list, but I am failing to copy all .deb files together ...

To reach this aim a found this two lines in a debian book:

COLUMNS=200 dpkg -l | grep '^ii' | awk '{ print $2 }' > /tmp/pkgliste
cat /tmp/pkgliste | xargs apt-get --download-only --reinstall -y --force-yes install


It look like the first line works. The file pkglist contained the desired packages.
The second comnand should ensure that all packages get downloaded to the folder /var/cache/apt/archives

Now the problem starts,this folder was emtpy! It doesn't contain the .deb files? 
I also noticed during the previous installation of the packages with synaptic from the DVD's. The .deb files never got cached in this folder? I also checked the setting in synaptic which look correctly.

May this cache directory only get used if you donwnloading the files from Internet?

Unfortunately, I have only a ISDN connection (fastet available connection!), like I live and work in a rulal part of Namibia (Africa). Forthermore I have only Internet access from my windows PC (usb-isdn modem), and not directly from the linux server. 

Somewhere I read,may  the apt-move command can help, to extract these packages from the repository-DVDs, but until know I failt even with this command.

After I have read for hours some forums, to find a solution, I  don't know anymore, how should I continue?

Help would be appreciated !

Philipp
([www.schoolnet.na](www.schoolnet.na))

---

### Post by Philipp99 on 2007-03-09
Meanwhile, I found the .deb files ...

Like I am new with Ubuntu I didn't know that the .deb files are the DVD in the spool folder. First I thought they are packaged in Packges.gz file ;-)

Now I wrote this script, which solve the issue :

# check if the folder is there 
if ! [ -d $LOCAL_DIR ]; then  
	mkdir $LOCAL_DIR
fi
echo "copy installed .deb from the DVD(s) to a local directory"

# generate package list, if it not already there 
if ! [ -e $PACKAGE_LIST ]; then  
	COLUMNS=200 dpkg -l | grep '^ii'  | awk '{ print $2 }'  > $PACKAGE_LIST
fi

# get the filepath(s) for the packages and save the output to /tmp/list
echo '' > /tmp/list
for PACKAGES in `cat $PACKAGE_LIST` ; do
	apt-cache show $PACKAGES | grep Filename | awk '{ print $2 }' >> /tmp/list
done

COUNT=`cat $PACKAGE_LIST | wc -l` 
echo   "$COUNT package(s) available ..."


# Copy files from the DVD 
echo "Please insert DVD ROM, and press <enter>"
read -e
mount /cdrom
cd /cdrom

for ENTRY in  `cat /tmp/list` ; do
	if [ -e ./$ENTRY ]; then
		cp ./$ENTRY  $LOCAL_DIR
		echo "$ENTRY copy ..."
	fi 
done
cd /
umount /cdrom
eject

You must run the script for every DVD, which you used for the previouses installation. After that you find all needed *.deb packages in the folder  $LOCAL_DIR.

with the command, you can write the Packages.gz file:

cd $LOCAL_DIR
/usr/bin/dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

Please notice this script is a first draft version, which I haven't tested in real enviroment. Anyway, May somebody can use it ? 

Philipp

---

