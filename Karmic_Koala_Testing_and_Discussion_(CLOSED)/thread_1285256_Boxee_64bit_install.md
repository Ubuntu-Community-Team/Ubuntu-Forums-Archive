---
title: "Boxee 64bit install"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by seamuso on 2009-10-07
[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310) -

All the good parts from the initial link:

Nitro's script takes care of most of it ..

```

#!/bin/sh
if [ ! $( which curl ) ]; then
sudo apt-get install -yq curl
fi

curl -s http://apt.boxee.tv/dists/intrepid/main/binary-i386/Packages.gz > /tmp/boxee_packages.gz
LATEST=$(zcat /tmp/boxee_packages.gz | grep Version | awk '{v=0;for (i = 1; i <= NF; i++) if ($2 > v) v = $2};END{print v}')

if dpkg -l boxee ; then
   CURRENT=$(dpkg -s boxee | awk '/Version/ {print $2}')
else
   CURRENT="0"
fi

echo Current version=$CURRENT
echo Latest version=$LATEST

if dpkg --compare-versions "$LATEST" gt "$CURRENT"; then
   echo Going to install/upgrade
   FILENAME=$(zcat /tmp/boxee_packages.gz | grep $LATEST | awk '/Filename/ {print $2}')
   echo Downloading $FILENAME
   wget http://apt.boxee.tv/$FILENAME -O /tmp/boxee_latest.deb
   echo Installing deb
   sudo dpkg -i --force-all  /tmp/boxee_latest.deb
   rm /tmp/boxee_latest.deb
   rm /tmp/boxee_packages.gz

   echo Installing libraries using getlibs
   if [ ! $( which getlibs ) ]; then
      wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb -O /tmp/getlibs-all.deb
      sudo dpkg -i /tmp/getlibs-all.deb
      rm /tmp/getlibs-all.deb
   fi
   getlibs /opt/boxee/Boxee

else
   echo No upgrade needed
fi

```

followup with

```
 sudo apt-get install lib32nss-mdns
```

and

```

wget http://ubuntu.osuosl.org/ubuntu/pool/universe/l/lzo/liblzo1_1.08-3_i386.deb

sudo getlibs -i <path-to>/liblzo1_1.08-3_i386.deb

```

and fix a locale error in line 11 of /opt/boxee/run-boxee-desktop

```

LC_ALL="en.gb"

```

change the above to match your correct locale info, mine is

```

LC_ALL="en_US.utf8"

```

Your mileage may vary, but it's working for me :)

---

### Post by nhasian on 2009-10-07
thanks for the post.  Do you know when the native 64 bit build of Boxee will be available?  I heard it was scheduled for the end of the year...

---

### Post by Nirro on 2009-10-07
There is a better version of the script, cleaner and shorter, by dustywilson.

```
#!/bin/sh
if [ "`which getlibs`" == "" ]; then
  wget -O /tmp/getlibs-all-$$.deb http://frozenfox.freehostia.com/cappy/getlibs-all.deb
  sudo dpkg -i /tmp/getlibs-all-$$.deb
  rm /tmp/getlibs-all-$$.deb
fi

wget -qO /tmp/boxee-packages-$$.gz http://apt.boxee.tv/dists/jaunty/main/binary-i386/Packages.gz
LATEST=`zgrep Version /tmp/boxee-packages-$$.gz | awk '{v=0; for (i = 1; i <= NF; i++) if ($2 > v) v = $2}; END {print v}'`
echo "LATEST: $LATEST"
CURRENT=`dpkg -s boxee 2> /dev/null | awk '/Version/ {print $2}'`
echo "CURRENT: $CURRENT"

if [ "$LATEST" != "$CURRENT" ]; then
  wget -O /tmp/boxee-$$.deb http://apt.boxee.tv/`zgrep Filename /tmp/boxee-packages-$$.gz | tail -n1 | awk '{print $2}'`
  sudo dpkg -i --force-all /tmp/boxee-$$.deb
  rm /tmp/boxee-$$.deb
  getlibs /opt/boxee/Boxee
fi

rm /tmp/boxee-packages-$$.gz
```

remember to run the script occasionally, to upgrade when a new version available.

---

