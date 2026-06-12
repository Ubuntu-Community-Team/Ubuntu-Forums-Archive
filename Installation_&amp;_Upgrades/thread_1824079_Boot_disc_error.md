---
title: "Boot disc error"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by FranzJoseph on 2011-08-13
I know this is an issue that has been addressed several times, but after burning loads of cds, checking the hashes and stuff, I still couldn't get it to work and I resorted to installing it through Windows. Is there anyting I can do to fix this problem ? My laptop is a HP Compaq 6710, and the Kubuntu version is the latest one (11.04). Thank You in advance for your support.

---

### Post by oldfred on 2011-08-13
Welcome to the forums.

Do you have Windows 7? If so you probably have all four primary partitions used to make it difficult to use any other system.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by allwimb on 2011-08-13
Sometimes you need to disable acpi and to check noapic too.

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by FranzJoseph on 2011-08-13
No, I've got XP. I'm pretty sure the partitions are ok, since I've done them without Windows. As for acpi and noapic ... Well ... How do I do that  ? I'm kind of a newbie ...

---

