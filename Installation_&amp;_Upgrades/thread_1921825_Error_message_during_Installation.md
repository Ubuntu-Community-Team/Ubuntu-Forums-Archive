---
title: "Error message during Installation"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by SHINRA SOLDIER on 2012-02-07
Hey guys, looking for some help. I keep getting an error message during installation using Wubi. Installation gets so far then I get an error message saying "Permission Denied". Ive tried running it as an administrator but same result.

Any ideas please?

---

### Post by Rafterman414 on 2012-02-07
This has been posted in the forums before. Try downloading the wubi installer and the Ubuntu iso that you would like and put both of those in the same directory. Then when you run the wubi.exe installer it should use the iso you downloaded as the installation source. Some people have experienced success with this after getting the permission denied error.

---

### Post by bcbc on 2012-02-07
+1 regarding installing with separate ISO. This is generally the best method.

Also check bug [lpbug]862003[/lpbug]. This has been fairly common and is a false error message on a successful install. 

But if you need help you have to post your log file because wubi messages don't generally tell enough of the story. Look in the %temp% directory for the log file (wubi-nn.nn-revnnn.log)

---

### Post by SHINRA SOLDIER on 2012-02-07
> **Rafterman414 said:**
> This has been posted in the forums before. Try downloading the wubi installer and the Ubuntu iso that you would like and put both of those in the same directory. Then when you run the wubi.exe installer it should use the iso you downloaded as the installation source. Some people have experienced success with this after getting the permission denied error.
hi thanks for your reply I'll give that a go. apologies for the repeat post.

---

### Post by Rafterman414 on 2012-02-07
Good luck, I have never actually used wubi but I have read some posts where using the iso fixed the issue. I am not sure what causes it I am guessing something with the wubi installer not being able to access the directory where the temporary install files are located.

---

### Post by SHINRA SOLDIER on 2012-02-07
> **Rafterman414 said:**
> Good luck, I have never actually used wubi but I have read some posts where using the iso fixed the issue. I am not sure what causes it I am guessing something with the wubi installer not being able to access the directory where the temporary install files are located.


worked like a charm, thanks for your help mate! this has been wrecking my head for a while.

Thanks again

---

### Post by Rafterman414 on 2012-02-07
Glad to hear it worked. Don't forget to mark the thread as solved.

---

