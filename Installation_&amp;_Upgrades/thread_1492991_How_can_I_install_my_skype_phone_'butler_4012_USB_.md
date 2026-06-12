---
title: "How can I install my skype phone: 'butler 4012 USB voip' with 'Skiputler'?"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by joept on 2010-05-25
Hello,

I am new here, I have Ubuntu: 10.04. And I would like install my skype phone: 'Butler 4012 USB voip. I I have  read you can do that with: Skiputler'

See: [http://ubuntuforums.org/showthread.php?t=1063793](http://ubuntuforums.org/showthread.php?t=1063793)

How can I install, Skiputler?
I do not know what to do. It's in the install file:

> Introduction:
-------------
  - TODO -

Requested - Linux:
------------------
  * glib-2.0 and its development package (libglib2.0-dev on Debian)
  * dbus-glib-1 and its development package (libdbus-glib-1-dev on  Debian)
  * libusb-0.1 and its development package (libusb-dev on Debian)
  * Skype for Linux; version 2.0 or later  ([http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/))
  * working D-Bus system ([http://dbus.freedesktop.org/](http://dbus.freedesktop.org/))

  * The USB device must be accesible by the user running Skype and  skiputler.
    Write a file /etc/udev/rules.d/10-local.rules with this content:

      ATTRS{idVendor}=="0e6a", ATTRS{idProduct}=="6002", GROUP="plugdev"

  * Make sure the user belongs to the "plugdev" group

Requested - Os X:
-----------------
 * dbus-glib-1 (e.g. "sudo port install dbus-glib-1" - see [http://www.macports.org/)]("http://www.macports.org/%29")
 * libusb-0.1 (e.g. "sudo port install libusb-legacy")
 * Skype for Os X; version 2.7.0.330 or later  ([http://www.skype.com/download/skype/macosx/](http://www.skype.com/download/skype/macosx/))
 * Skype API Framework  ([https://developer.skype.com/Docs/ApiDoc/Skype_API_on_Mac/):]("https://developer.skype.com/Docs/ApiDoc/Skype_API_on_Mac/%29:")
   Mount disk image (dmg) and copy the folder "Skype.framework" to  /System/Library/Frameworks
 * osxbridge from [https://sourceforge....kiputler/files/]("https://sourceforge.net/projects/skiputler/files/")

Installation:
-------------
    $ cd src
    $ make
  as root:
    $ make install

Running - Linux:
----------------
    $ skiputler

  * IMPOPRTANT: skiputler and Skype must be run by the same user.

  * Use "nohup" to run it in a daemon like behaviour:
    $ nohup skipulter &

  * Change loglevel (1=report only errors, 2=informative, 3=debugging):
    $ skipulter --loglevel 1

Running - Os X:
---------------
  * Make sure DBUS session agent is running:
    $ sudo launchctl load -w /Library/LaunchAgents

  * Run osxbridge in a "crash safe" manner:
    $ while true ; do ./osxbridge ; done

    $ skiputler
 
  * IMPOPRTANT: skiputler and Skype must be run by the same user.

  * Use "nohup" to run it in a daemon like behaviour:
    $ nohup skipulter &

  * Change loglevel (1=report only errors, 2=informative, 3=debugging):
    $ skipulter --loglevel 1

Error reporting:
----------------
[https://sourceforge....15&atid=1126639]("https://sourceforge.net/tracker/?group_id=250215&atid=1126639")Thanks, voor the support.

---

