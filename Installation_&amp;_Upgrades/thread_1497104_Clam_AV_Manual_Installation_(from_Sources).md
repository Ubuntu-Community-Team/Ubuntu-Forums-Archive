---
title: "Clam AV Manual Installation (from Sources)"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by er_mahavir on 2010-05-30
**[SIZE=3]Introduction:[/SIZE]**

An open source anti-virus to scan windows partition.

clamav is a command line tool.
clamtk can be used as its frontend.

**[SIZE=3]Need of this post[/SIZE]**
* Upgrade to clamav independent of distro-based release.
* The clamav package that is present in official repository of Ubuntu 9.10 is outdated.

**[SIZE=3]Clam AV Compilation and Installation[/SIZE]**
1. Download clamav-0.96.1.tar.gz or latest version if available to your home folder.
2. Open shell and give following commands.
  ```

  cd ~/
  tar -xvf clamav-0.96.1.tar.gz
  sudo mkdir /usr/local/built_clamav
  sudo chmod 777 /usr/local/built_clamav
  cd clamav-0.96.1
  ./configure --prefix=/usr/local/built_clamav
  make 
  make install
  

```3. As we have installed clamav at a custom location so edit  ~/.bashrc and add the following:
 Add /usr/local/built_clamav/bin/ in the path
       ```
export PATH=/usr/local/built_clamav/bin:$PATH
``` Add /usr/local/built_clamav/share/man in the MANPATH
    ```
export MANPATH=/usr/local/built_clamav/share/man:$MANPATH
```**[SIZE=3]Clam AV virus database update[/SIZE]**
First, let us see the problems that I encountered while updating the virus database.

Run freshclam to update the database. Following error will be encountered:
```
freshclam
ERROR: Please edit the example config file /usr/local/built_clamav/etc/freshclam.conf
ERROR: Can't open/parse the config file /usr/local/built_clamav/etc/freshclam.conf

```[SIZE=2]Resolving the issue:[/SIZE]
Edit /usr/local/built_clamav/etc/freshclam.conf using your favorite editor:
    ```
emacs -nw /usr/local/built_clamav/etc/freshclam.conf
```Comment/Uncomment & Modify the following lines in the file
```
    # Example                           
    DatabaseDirectory /usr/local/built_clamav/var/lib/clamav
    UpdateLogFile /usr/local/built_clamav/var/log/freshclam.log

```Exit the editor
[SIZE=2]Create the required directories  [/SIZE]
```
    
   mkdir -p /usr/local/built_clamav/var/log
   mkdir -p /usr/local/built_clamav/var/lib

```Now, run freshclam to update virus defintions and it should be able to download the virus definitions
```
freshclam
```**[SIZE=3]Clam AV GUI  = clamtk[/SIZE]**

Note: As clamtk is written using PERL, so there is no need of compilation

1. Download clamtk-4.26.tar.gz to your home folder.
2. Open shell and give following commands.
```
 
  cd ~/
  tar -xvf clamtk-4.26.tar.gz
  mv clamtk-4.26 /usr/local/built_clamav/share/

```3. As we have installed clamtk at a custom location so edit ~/.bashrc.
 Add /usr/local/built_clamav/share/clamtk-4.26/ in the path
```
export PATH=/usr/local/built_clamav/share/clamtk-4.26/:$PATH
```3.On running the clamtk gui, following error was shown
```

clamtk
Can't locate ClamTk/Prefs.pm ...

```Resolve by doing following steps:
  ```

cd /usr/local/built_clamav/share/clamtk-4.26/
mv lib/ ClamTk/

```Now, edit /usr/local/built_clamav/share/clamtk-4.26/clamtk file using your favorite editor 
```
emacs /usr/local/built_clamav/share/clamtk-4.26/clamtk
```Add following line
```
use lib    '/usr/local/built_clamav/share/clamtk-4.26/';
```Finally, add shortcut to desktop:
  ```
cp /usr/local/built_clamav/share/clamtk-4.26/clamtk.desktop ~/Desktop/
```A "Virus Scanner" shortcut will be present on the desktop. 

Double-click the launcher to run clamtk. A warning message comes up. 

Choose "Mark as trusted" when pop-up comes up.

---

