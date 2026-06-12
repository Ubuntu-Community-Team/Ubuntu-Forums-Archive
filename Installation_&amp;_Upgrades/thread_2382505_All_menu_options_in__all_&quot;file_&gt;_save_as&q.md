---
title: "All menu options in  all &quot;file &gt; save as&quot;-menus black and unreadable. How to repair?"
date: 2018-01-14
forum: Installation &amp; Upgrades
---

### Post by siggi2 on 2018-01-14
Hi,

I am using Ubuntu 16.04 Unity and _can barely decipher the "file > save as" menu options of all programs_, e.g., LibreOffice Writer, see MenuWriterAfter.jpg. How can I make these menu options visible like they are in a fresh install before the necessary first updates, see MenuWriterBefore.jpg?

Thank you,

siggi

---

### Post by siggi2 on 2018-01-15
Solved :D 
Maybe there is an easier solution, maybe it is gone after the next big update, but it works beautifully right now:

I modified the bugfix  [https://bugs.launchpad.net/ubuntu/+source/ubuntu-themes/+bug/1212712]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-themes/+bug/1212712")  for my own problem:

1. Opened */usr/share/themes/Ambiance/gtk-2.0/gtkrc* with *sudo nano*
2. Searched for line containing: style "menu"
3. This line looked like this: style "menu" = "dark" {
4. Now changed it to: 5. style "menu" = "white" {
5. Saved the changes and rebooted

---

