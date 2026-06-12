---
title: "Vuze V4.8.0.0/4 az3 partially fails on startup  after upgrade to Ubuntu 12.10"
date: 2012-11-03
forum: Installation &amp; Upgrades
---

### Post by pilot4fun on 2012-11-03
I upgraded to Ubuntu 12.10 (64-bit system before and after.) Vuze appears to start correctly but search does not work. Thought it was a Java problem, but Java reports it is installed correctly. (Java SE 7 update 09.)

When I execute Azerus startup in a window I get the following:
Starting Azureus...
Suitable java version found [java =
1.7.0_09]
Configuring environment...
Java exec found in PATH. Verifying...

/home/gyoutz/vuze/azureus:
line 116: 6045 Aborted (core dumped)
${JAVA_PROGRAM_DIR}java "${JAVA_ARGS}" -cp "${CLASSPATH}"
-Djava.library.path="${PROGRAM_DIR}"
-Dazureus.install.path="${PROGRAM_DIR}"
-Dazureus.script="$0" $JAVA_PROPS "$@" >
~/azScript
Browser check
failed with: InvocationTargetException, No more handles [Unknown
Mozilla path (MOZILLA_FIVE_HOME not set)]
Auto-scanning for GRE/XULRunner. You
can skip this by appending the GRE path to LD_LIBRARY_PATH and
setting MOZILLA_FIVE_HOME.
checking /usr/lib/firefox-addons for
GRE
Can not use GRE from
/usr/lib/firefox-addons because it's missing libxpcom.so.
checking /usr/lib/firefox for GRE
GRE found at /usr/lib/firefox.
Loading Azureus:
...

Result is that Vuze appears to run but searches do nothing at all.....

Also thought it might be a Firefox (Mozilla) issue so re-installed Firefox, but no change.

Can someone give me a hint as to what the problem might be and how to repair it?

Thanks from a not-too-technical Linux user.....

---

### Post by lhail on 2012-11-09
I have the same issue, in fact running a search in Vuze will make it crash after eating all my processor load.
I can still use Transmission Bittorrent with no issues.
I have 32-bit Ubuntu installed

---

