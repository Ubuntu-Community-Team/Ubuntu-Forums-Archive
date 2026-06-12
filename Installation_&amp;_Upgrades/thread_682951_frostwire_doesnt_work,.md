---
title: "frostwire doesnt work,"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by hasanyaman on 2008-01-30
hi my friends 
my problem is about frostwire i downloaded it from internet and installed... i am running the application from applications/internet/frostwire but doesnt happen anything i thought it causes from java adition and installed java 1.6 but didnt work..because of being a new user of ubuntu 7.10 i dont know much 
i want to paste the error here from the terminal or console but i dont know what to write 
to the console to work the frostwire
please help

---

### Post by taurus on 2008-01-30
Let's see if you have the right version of java running as default on your machine.  Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
java -version
```
Otherwise, try running frostwire from a terminal to see exactly what the error message is.

```
frostwire
```

---

### Post by hasanyaman on 2008-01-30
when i wrote frostwire to the console it gives syntax error 


AND THIS IS THE VERSION OF JAVA

java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

---

### Post by taurus on 2008-01-30
And what happens when you run frostwire from a terminal?

---

### Post by hasanyaman on 2008-01-30
i dont know how i can run frostwire from terminal(which command).because i am a new user of ubuntu but if you can say which, i can paste the error here

---

### Post by taurus on 2008-01-30
If you look at my post #2, it says

```
frostwire
```
You can cut the text with the left button of your mouse and paste it here with the middle button or the little track.

---

### Post by hasanyaman on 2008-01-30
runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")

---

### Post by taurus on 2008-01-30
I am sure that program is in /usr/bin so can you post the output of this command from a terminal?  It probably has /bin/sh in there instead of /bin/bash in line 44.

```
cat /usr/bin/runFrost.sh
```

---

### Post by hasanyaman on 2008-01-30
cat: /usr/bin/runFrost.sh: No such file or directory

---

### Post by taurus on 2008-01-30
```
whereis runFrost.sh
```

---

### Post by hasanyaman on 2008-01-30
runFrost:

---

### Post by taurus on 2008-01-30
Run this then.

```
sudo find / -name runFrost* -print
```

By the way, how did you install frostwire?  Did you install it through Add/Remove, synaptic, or apt-get/aptitude or did you install it by hand?

---

### Post by hasanyaman on 2008-01-30
/usr/lib/frostwire/runFrost.sh.~1~
/usr/lib/frostwire/runFrost.sh

i installed it with  apt-get/aptitude

---

### Post by taurus on 2008-01-30
```
cat /usr/lib/frostwire/runFrost.sh
```

---

### Post by hasanyaman on 2008-01-30
this is really long



[B][PHP]#!/bin/sh
#
# Runs FrostWire.  This script must be executed in your FristWire
# install directory. (/usr/lib/frostwire)
# Currently mantained by Gubatron
# Last update: May 23rd 2006

# this should allow starting limewire from
# gui-based explorer interfaces
cd "`dirname "$0"`"

# try to discover java
MSG0="Loading FrostWire:"
MSG1="Starting FrostWire..."
MSG2="Java exec found in "
MSG3="OOPS, your java version is too old "
MSG4="You need to upgrade to JRE 1.4.x or newer from http://www.java.com"
MSG5="Suitable java version found "
MSG6="Configuring environment..."
MSG7="OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com "
MSG8="OOPS, unable to locate java exec in "
MSG9=" hierarchy"
MSG10="Java exec not found in PATH, starting auto-search..."
MSG11="Java exec found in PATH. Verifying..."

look_for_java() {
 JAVADIR=/usr/lib  
 if look_for_javaImpl ; then
    return 0
 fi 
 JAVADIR=/usr/java
 if look_for_javaImpl ; then
       return 0
 fi
 JAVADIR=/opt
 if look_for_javaImpl ; then
       return 0
 fi
 return 1
}

look_for_javaImpl() {
  IFS=$'\n'
  potential_java_dirs=(`ls -d1 "$JAVADIR"/j* | sort | tac`)
  for D in "${potential_java_dirs[@]}"; do
    if [[ -d "$D" && -x "$D/bin/java" ]]; then
      JAVA_PROGRAM_DIR="$D/bin/"
      echo $MSG2 $JAVA_PROGRAM_DIR
      if check_version ; then
        return 0
      fi
    fi
  done
  echo $MSG8 "${JAVADIR}/" $MSG9 ; echo $MSG4
  return 1 
}

check_version() {
  # short-circuit gcj
  ISGCJ=`${JAVA_PROGRAM_DIR}java -version 2>&1 | grep -i gcj`
  if [ "$ISGCJ" != "" ] ; then
      echo $MSG7
      return 1
  fi

  JAVA_HEADER=`${JAVA_PROGRAM_DIR}java -version 2>&1 | head -n 1`
  JAVA_IMPL=`echo ${JAVA_HEADER} | cut -f1 -d' '`
  if [ "$JAVA_IMPL" = "java" ] ; then
    VERSION=`echo ${JAVA_HEADER} | sed "s/java version \"\(.*\)\"/\1/"`
    if echo $VERSION | grep "^1.[0-3]" ; then
      echo $MSG3 "[${JAVA_PROGRAM_DIR}java = ${VERSION}]" ; echo $MSG4
      return 1
    else
      echo $MSG5 "[${JAVA_PROGRAM_DIR}java = ${VERSION}]" ; echo $MSG6
      return 0        
    fi
  else
    echo $MSG7 "[${JAVA_PROGRAM_DIR}java = ${JAVA_IMPL}]" ; echo $MSG4
    return 1
  fi
}

echo $MSG1

# locate and test the java executable
if [ `uname` = "Linux" ]; then
  if ! command -v java &>/dev/null; then
    echo $MSG10
    if ! look_for_java ; then
      exit 1
    fi
  else
    echo $MSG11
    if ! check_version ; then
      if ! look_for_java ; then
        exit 1
      fi
    fi
  fi
else
  JAVA_PROGRAM_DIR=""
fi

echo $MSG0

export J2SE_PREEMPTCLOSE=1

${JAVA_PROGRAM_DIR}java  -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. -jar FrostWire.jar
if [ $? -ne 0 ]; then
    echo 
    echo "******************************************************************"
    echo "Something went wrong with FrostWire."
    echo "Maybe you're using the wrong version of Java?"
    echo "(Frostwire is tested against and works best with with Sun's JRE, Java 1.4+)"
    echo "The version of Java in your PATH is:"
    java -version
    echo
    echo "If you keep having trouble please come to our forum at"
    echo "http://www.frostwire.com/forum/forum.php to find the answers"
    echo "We're also available through irc at irc.peercommons.net on the #main channel"
    echo 
fi[/PHP][/B]

---

### Post by hasanyaman on 2008-01-30
isnt there anybody who knows how i can fix this error or work frostwire... what the outputs above mean..
i am waiting your answers

---

### Post by erginemr on 2008-01-31
Hi there, 

I am also running Frostwire with no issues whatsoever, have the same version of Java, but I had installed it from the Debian installer package on their web page. So, I suggest you to remove it from Synaptic, download the latest version from:

[http://www.frostwire.com/?id=downloads](http://www.frostwire.com/?id=downloads)

and install that package instead.

---

### Post by hasanyaman on 2008-01-31
yes yes  it works!! thanks a lot

---

### Post by erginemr on 2008-01-31
Great! :)

Take care and have fun with Ubuntu!

---

