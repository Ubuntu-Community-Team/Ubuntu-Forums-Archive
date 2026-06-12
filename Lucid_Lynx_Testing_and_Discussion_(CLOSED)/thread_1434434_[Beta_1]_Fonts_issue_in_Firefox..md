---
title: "[Beta 1] Fonts issue in Firefox."
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Sslaxx on 2010-03-20
Pretty minor issue, really, but the '6' and '9' are looking strange in Firefox. Maybe other applications using DejaVu Sans too, but I haven't (yet) noticed, nor have I noticed any other characters looking odd (yet).

---

### Post by Sslaxx on 2010-03-20
Just realised some sites no longer have bold text - probably connected to this issue.

---

### Post by phibxr on 2010-03-20
> **Sslaxx said:**
> Pretty minor issue, really, but the '6' and '9' are looking strange in Firefox. Maybe other applications using DejaVu Sans too, but I haven't (yet) noticed, nor have I noticed any other characters looking odd (yet).

Would it be possible to provide a screenshot of this issue?

---

### Post by Sslaxx on 2010-03-20
Sure, see the attachment. I've ringed around a few of the issues I've noticed ('6', '9', 'C' seems a little odd and no bold text). It depends on the website. For example, the one in the attachment shown. Some parts of the front page of these forums show the issue, so does Facebook.

---

### Post by Sslaxx on 2010-03-20
Unchecking the "Allow pages to choose their own fonts..." option from Preferences->Content->Advanced resolves the issue. Whatever font sites is picking isn't working as it should.

---

### Post by NRK on 2010-03-31
I have this issue too, mainly in facebook, using both Firefox and Chrome/Chromium. I hope that it will be fixed soon :(

---

### Post by psyke83 on 2010-03-31
> **Sslaxx said:**
> Pretty minor issue, really, but the '6' and '9' are looking strange in Firefox. Maybe other applications using DejaVu Sans too, but I haven't (yet) noticed, nor have I noticed any other characters looking odd (yet).

See: [http://ubuntuforums.org/showpost.php?p=9010164&postcount=10](http://ubuntuforums.org/showpost.php?p=9010164&postcount=10)

---

### Post by jaco223 on 2010-03-31
Originally Posted by **lovinglinux**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8704533#post8704533")                 
                 [I]Try this:

     Code:
     gedit ~/.fonts.conf 
then replace the content of that file with this:

     Code:
     <?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig> 
Save it and restart Firefox.

Please report if that works or not. It seems this will be a very common  question.

Try this, it worked for me in firefox. There is also a issue with chromium, there is a bug report for chromium dating back to 2009. Don't know why it hasn't been resolved yet, because there is a font issue. I have reverted to using firefox until things are fixed with chromium
[/I]

---

