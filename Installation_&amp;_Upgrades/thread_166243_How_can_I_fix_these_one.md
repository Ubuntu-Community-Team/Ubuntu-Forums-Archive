---
title: "How can I fix these one?"
date: 2006-04-26
forum: Installation &amp; Upgrades
---

### Post by j_a_c_k_s_o_n on 2006-04-26
i can now open .exe files in UBUNTU 5.10, but i do having some troubles.. my installation fails because of accessing "c:\windows\dll" cause it does not exist..could anyone help me here pls....

---

### Post by Sef on 2006-04-26
> i can now open .exe files in UBUNTU 5.10, but i do having some troubles.. my installation fails because of accessing "c:\windows\dll" cause it does not exist..could anyone help me here pls....

1) For an install, you just need to put the cd in and it boots up.  You do not need to open any .exe files.  

2) It sounds like Windows is up, and if so, then put the disk in the cd, but do not close.  Restart the computer.  The BIOS should pick up your disk, and you should be at the start up install screen.  If you are not, then likely you have one of these problems:

1) The cd-rom/rw is not set to boot before the hard disk.  Go into the BIOS and change it.  To get into the BIOS, usually you push either esc, F2, or delete.  Upon starting it will tell you what to push to get into the BIOS.

2) The cd or the burn was bad.  Reburn on a new cd.

3) Md5sum the downloaded iso.  This makes sure it was downloaded correctly.  To md5sum from a command prompt or terminal > cd to_where_the_iso_file_was_downloaded > if it matches the one given to you by the download site, you have a good file.  If not, redownload.

4) You burned the file and not the iso.   For windows, go to this site and download the isoburner.

[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm")

---

