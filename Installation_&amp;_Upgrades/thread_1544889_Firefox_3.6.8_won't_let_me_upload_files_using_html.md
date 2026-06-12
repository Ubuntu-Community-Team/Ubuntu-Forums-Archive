---
title: "Firefox 3.6.8 won't let me upload files using html form"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by wiredman on 2010-08-03
Hi Everyone:

I'm having a weird problem while uploading a file using a standard html form in Firefox 3.6.8(No extensions, except for the preloaded ones : Ubuntu Firefox modifications 0.9Rc2, mouse gesture redox 3.0.2 ).

Anytime I try to upload a file whether on my localhost or at a website that offers a form with an input file, it fails.

I'm just using test files, like small images.

I've reinstalled my firefox, because I got this problem since 9.10 and now that I've upgraded to Lucid Lynx, I still have this issue.

That's why I decided to do a fresh re-install using the same package I've downloaded previously when I did the ugprade. However, I still have the same result, the file never uploads to the server.

This happens when I use a simple html form with enctype="multipart/form-data".

**Though, when I use any other browser, like chrome, chromium, opera they just work fine.**
 
Any ideas on how Could I solve this problem?

At my localhost, this is my code in one page, if you want to take a look, but as I say even with other websites the problem is happening too.

Btw, the temp folders have written permissions (777)

[PHP]error_reporting(E_ALL);
ini_set('display_errors','On');
$currentDir = dirname(__FILE__);

 if(isset($_POST['submit'])) {
  if(!empty($_FILES)) {
    if(is_uploaded_file($_FILES['fileme']['tmp_name'])){
      $tmpName = tempnam($currentDir."/img/tmp/","PS");
      move_uploaded_file($_FILES['fileme']['tmp_name'],$tmpName);
      }
    }
 }   
[/PHP]
[PHP]
<!DOCTYPE head PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
</head>
<body>

<form action="test-move-upload.php" method="post" enctype="multipart/form-data" name="product" id="product">
<input type="file" name="fileme" /><br />
<input type="submit" name="submit" value="submit" /> 
</form>
</body>
</html>[/PHP]

---

### Post by lovinglinux on 2010-08-03
Mouse Gestures Redox is not preloaded and is not compatible with Firefox 3.6. Last time it was updated was January 2009, so I would start by disabling it.

I did a test here with a clean profile of Firefox 3.6.8 and after forcing the installation of Mouse Gestures Redox the browser doesn't even start.

BTW, it messed with the profile too. I had to delete the profile with sudo to get rid of it. So you might need to verify if your profile is not corrupted or has the wrong permissions.

---

### Post by wiredman on 2010-08-04
Thanks for your response:

I uninstalled all firefox extensions, and I searched for any profiles(#locate firefox)  and removed everything related to firefox, I also did a complete removal of firefox and firefox branding and ubufox.

Then after a fresh install, I still have the same error.

I used the same script with chrome and there was no problem.

Is there something I could be missing, maybe a setting from about:config related to uploading files ?

Tmp folder is ok. Though since I'm using a prestashop store to test in the internet too, that shouldn't matter.

drwxrwxrwt  18 root root  68K 2010-08-04 01:12 tmp

I've tested gmail and I couldn't attach a file.

---

### Post by lovinglinux on 2010-08-04
Disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

I'm not sure this is the the problem, but this is the only thing I can't think of that could mess with a clean profile.

---

### Post by wiredman on 2010-08-07
Thanks Thanks Thanks ....!

This really solve my problem, you're a life savior :D

Though I really found weird that this problem was affecting the ability to upload files.

Well thanks again lovinglinux.

---

### Post by lovinglinux on 2010-08-07
> **wiredman said:**
> Thanks Thanks Thanks ....!

This really solve my problem, you're a life savior :D

Though I really found weird that this problem was affecting the ability to upload files.

Well thanks again lovinglinux.

You are welcome.

---

