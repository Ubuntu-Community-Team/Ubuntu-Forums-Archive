---
title: "[SOLVED] login interrupted"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by benvantende on 2008-10-04
Hi,

When I login I get as far as 4 out of 5 icons after which the procedure quits and I am confronted with the login screen again. When I shutdown I can see a message saying that kdm-kde4 is not running. I upgraded from Hardy to Ibex so there might be a problem there. I am guessing kdm-kde4 is not needed anymore. Can anyone help me out here?

gRTz

ben

---

### Post by iponeverything on 2008-10-04
You can try this if you want..

Do a <CTL><ALT><F2>
login and do:

useradd <newname>
passwd <newpasswd>

then go back to login screen at <CTL><ALT><F6> or maybe <CTL><ALT><F7>

and login with the new name. Move your personal stuff over to new account.

once get it way that want it do this in a terminal:
where original_account = the broken account
      new_account      = your new account created above

cd /home
sudo mv original_account original_account.old
sudo mv new_account original_account
sudo chown -R orginal_account.orginial_account   orginal_account

---

### Post by benvantende on 2008-10-04
Hey,

tHNx for your reply. When I create a new user and login as that user I get stuck with a black screen and the X cursor. Nothing else happens. The necessary fles in the home dir are created. Could it be there are some incompatibilities in xorg, because that one is also pre-Intrepid. I tried to reconfigure xorg, but that only puts some default values in xorg.

gRTz

ben

---

### Post by benvantende on 2008-10-04
Hey,

It is definitely something to do with xorg. I generated a very basic xorg with xfix after all and that makes me able to log in with a low res only to show that my wireless intel 4965 and my bluetooth is not working :-( So once again I find myself in upgrade hell. How on earth am I getting this all to run?

gRTz

ben

---

