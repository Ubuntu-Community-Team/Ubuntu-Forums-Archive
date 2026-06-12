---
title: "Using disk Images"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by nocare on 2010-08-12
So I've been playing around with arch and ubuntu in virtual box, and after many... many installs i realized it'd be practical to just image the virtual drive and do it that way.

Now of course I could just copy the vdi file, but that's cheating. 

Kind of like what is normally done with norton ghost, however I don't have money to be buying it, and so it's left me curious about what utilities similar to ghost there are our there.

Any help would be appreciated, and thank you.

---

### Post by ubunterooster on 2010-08-12
[http://clonezilla.org/](http://clonezilla.org/)

**[COLOR=#3333ff]What is Clonezilla ?[/COLOR]  **
[INDENT]You're probably familiar with the popular proprietary commercial package [Norton Ghost®]("http://www.ghost.com/").  The problem with these kind of software packages is that it takes a lot  of time to massively clone systems to many computers. You've probably  also heard of Symantec's solution to this problem, [Symantec Ghost Corporate Edition®]("http://www.norton.com/")  with multicasting. Well, now there is an OpenSource clone system (OCS)  solution called Clonezilla with unicasting and multicasting!
  
  Clonezilla, based on [DRBL]("http://drbl.sf.net/"), [Partclone]("http://partclone.org/") and [udpcast]("http://udpcast.linux.lu/"), allows you to do bare metal backup and recovery. Two types of Clonezilla are available, [Clonezilla live]("http://clonezilla.org/clonezilla-live/") and [Clonezilla SE (server edition)]("http://clonezilla.org/clonezilla-server-edition/").  Clonezilla live is suitable for single machine backup and restore.  While Clonezilla SE is for massive deployment, it can clone many (40  plus!) computers simultaneously. Clonezilla saves and restores only used  blocks in the harddisk. This increases the clone efficiency. At the  NCHC's Classroom C, Clonezilla SE was used to clone 41 computers  simultaneously. It took only about 10 minutes to clone a 5.6 GBytes  system image to all 41 computers via multicasting![/INDENT]

---

### Post by nocare on 2010-08-13
I think this is exactly what I need, can't believe I haven't heard of it over the years ><

Thank's a lot, and i'll give it a  shot.

---

