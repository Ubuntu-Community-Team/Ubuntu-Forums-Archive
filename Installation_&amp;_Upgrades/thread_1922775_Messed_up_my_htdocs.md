---
title: "Messed up my htdocs"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by martin11ph on 2012-02-09
Hi guys, another blunder by me. Here's what I did:

1. I have an existing htdocs on my Windows partition and wanted to copy it to the htdocs in my Ubuntu partition.

2. I couldn't paste in /opt/lampp/htdocs

3. I used sudo cp ../../media/Drive2/xampp/htdocs /opt/lampp/htdocs. I got some errors at which I used -f and -r. Somewhere along the way, there was no error reported. I checked the filesystem but couldn't open the folders in htdocs.

4. I read somewhere that I should use gksu nautilus which I did. I was then able to access the folders in the htdocs. 

5. I turned on LAMPP and could access localhost and localhost/phpmyadmin but I couldn't access any of my pages. 

6. I did ls -ld and found out that the owner was listed as root probably due to my sudo cp.

7. I changed it via chown -hR to my user account.

8. Until now, I still cannot access my pages. When I open them in the browser, I get either

> 
**Warning**:  Unknown: failed to open stream: Permission denied in **Unknown** on line **0**

**Fatal error**:  Unknown: Failed opening required '/opt/lampp/htdocs/test/test.php' (include_path='.:/opt/lampp/lib/php') in **Unknown** on line **0**or > **Access forbidden!**

            You don't have permission to access the requested object.     It is either read-protected or not readable by the server.      
  If you think this is a server error, please contact the [EMAIL="you@example.com"]webmaster[/EMAIL].  
  **Error 403**

Result of ls -l is (same for all so I just pasted one):
> drwxrwxrwx  5 martin root   4096 2012-02-09 22:14  test

Hope someone can help. I've got a backup of the htdocs so I have no problem starting over if needed.

---

### Post by martin11ph on 2012-02-13
Bump.

---

### Post by martin11ph on 2012-02-15
Update: I tried copy pasting directly from Drive2 on normal nautilus to /opt/lampp/htdocs on gksu nautilus. It still does not work. Does it have something to do with the Windows permissions against Linux permissions? Hope someone can help. Thanks.

---

