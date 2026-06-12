---
title: "3 step guide to fst on karmic 32bit"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by c00kie55 on 2009-10-11
3 step guide to fst on karmic 32bit

i build this guide with help from here [http://ubuntuforums.org/showthread.php?t=557466](http://ubuntuforums.org/showthread.php?t=557466)


1) 
sudo apt-get install libjack0.100.0-dev libxml2-dev libsamplerate-dev libraptor-dev liblrdf-dev libglib2.0-dev libgtk2.0-dev libgnomecanvas2-dev liblo-dev libboost-dev libasound-dev libart-2.0-dev libxslt1-dev git-core qjackctl lashd liblash-dev wine1.2 wine1.2-dev build-essential scons libtool gettext

2)
git clone "git://repo.or.cz/fst.git"

cd fst
make

3) how to use 
./fst.exe /home/"your plugin folder"/pluginn.dll

now to get it working with lash you have to rename fst.exe to fst
 
sudo apt-get install lash-bin

./fst /home/"your pluginn folder"/pluginn.dll

you migth also want to copy your fst and fst.exe.so to usr/bin or usr/local/bin

for more fun try 
sudo apt-get install patchage 

nb i got this issue when using lash and fst
fixme:event:wait_for_withdrawn_state window 0x20036/5400005 wait timed out
work-around is restart qjackctl or close the vst before the project

hope i didnt forget something :guitar:

---

