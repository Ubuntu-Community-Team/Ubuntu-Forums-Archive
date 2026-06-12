---
title: "GnuPG loses my secret key after about 5-10 mins of logging in"
date: 2017-07-30
forum: MINT
---

### Post by tornadof3 on 2017-07-30
Hi
I am having a very strange problem here. I have used GnuPG for several years with no problems (eg with Enigmail/Thunderbird). Recently having major issues involving my secret key being removed from my keyring, for unknown reasons. Thankfully I have a backup.
So if I use either the command line or Gnu Privacy Assistant (GPA) or KGpg to create a new key pair, or if I import from my backup file, all looks well. I have my public and private keys, can encrypt/decrypt, enigmail works just fine. Wait a period of time (normally 5-10 mins), all of a sudden, my secret key is no longer on my keyring. Enigmail won't decrypt messages, GPA shows only my public keys in the keyring. Bizarre! Also, I then cannot import the secret key as the ~/.gnupg folder appears locked by some strange processes. My solution is to delete ~/.gnupg folder, re-import. Then all will work fine.

So I know this will be difficult to work out, so can people advise if a) anyone's ever heard of this sort of thing and b) what info should I post to help work out what the problem is?

Thanks in advance, sorry this sounds like one of those problems that will be difficult to solve.

Machine is Linux Mint 18.1 which uses the Ubuntu 16.04 packages.

---

### Post by ajgreeny on 2017-07-30
*Thread moved to **MINT**.* which is more appropriate and a better fit.

---

### Post by tornadof3 on 2017-08-13
So, after doing some research, I used `auditd` ([https://www.digitalocean.com/community/tutorials/how-to-use-the-linux-auditing-system-on-centos-7]("https://www.digitalocean.com/community/tutorials/how-to-use-the-linux-auditing-system-on-centos-7")) to monitor my /home/username/.gnupg folder. I deleted the .gnupg folder and re-imported my private keys so that I had a working GnuPG setup; it is usually 5-10 mins from this point before it stops working, and I finished re-importing and had my 'working' GnuPG setup from 12:09:18:

Here are some interesting logs:
```

username@localmachine:/var/log$ sudo aureport -f -i
<snip lines 1-75... from earlier and GNUPG working fine up until this point>
76. 13/08/17 12:15:35 .gnupg openat yes /bin/chown root 177
77. 13/08/17 12:15:35 trustdb.gpg fchownat yes /bin/chown root 178
78. 13/08/17 12:15:35 gpa.conf fchownat yes /bin/chown root 179
79. 13/08/17 12:15:35 private-keys-v1.d openat yes /bin/chown root 180
80. 13/08/17 12:15:35 4363804FC4D55B15D8D3C173314D19E289BBF456.key fchownat yes /bin/chown root 181
81. 13/08/17 12:15:35 22BAF8CCFC7EF031542F34DA2A5AB9A9205C410F.key fchownat yes /bin/chown root 182
82. 13/08/17 12:15:35 private-keys-v1.d fchownat yes /bin/chown root 183
83. 13/08/17 12:15:35 S.gpg-agent fchownat yes /bin/chown root 184
84. 13/08/17 12:15:35 pubring.kbx~ fchownat yes /bin/chown root 185
85. 13/08/17 12:15:35 pubring.kbx fchownat yes /bin/chown root 186
86. 13/08/17 12:15:35 S.dirmngr fchownat yes /bin/chown root 187
87. 13/08/17 12:15:35 crls.d openat yes /bin/chown root 188
88. 13/08/17 12:15:35 DIR.txt fchownat yes /bin/chown root 189
89. 13/08/17 12:15:35 crls.d fchownat yes /bin/chown root 190
90. 13/08/17 12:15:35 S.uiserver fchownat yes /bin/chown root 191
91. 13/08/17 12:15:35 .gnupg fchownat yes /bin/chown root 192
92. 13/08/17 12:16:02 .gnupg fchmodat yes /bin/chmod root 205
93. 13/08/17 12:16:02 .gnupg openat yes /bin/chmod root 206
94. 13/08/17 12:16:02 trustdb.gpg fchmodat yes /bin/chmod root 207
95. 13/08/17 12:16:02 gpa.conf fchmodat yes /bin/chmod root 208
96. 13/08/17 12:16:02 private-keys-v1.d fchmodat yes /bin/chmod root 209
97. 13/08/17 12:16:02 private-keys-v1.d openat yes /bin/chmod root 210
98. 13/08/17 12:16:02 4363804FC4D55B15D8D3C173314D19E289BBF456.key fchmodat yes /bin/chmod root 211
99. 13/08/17 12:16:02 22BAF8CCFC7EF031542F34DA2A5AB9A9205C410F.key fchmodat yes /bin/chmod root 212
100. 13/08/17 12:16:02 S.gpg-agent fchmodat yes /bin/chmod root 213
101. 13/08/17 12:16:02 pubring.kbx~ fchmodat yes /bin/chmod root 214
102. 13/08/17 12:16:02 pubring.kbx fchmodat yes /bin/chmod root 215
103. 13/08/17 12:16:02 S.dirmngr fchmodat yes /bin/chmod root 216
104. 13/08/17 12:16:02 crls.d fchmodat yes /bin/chmod root 217
105. 13/08/17 12:16:02 crls.d openat yes /bin/chmod root 218
106. 13/08/17 12:16:02 DIR.txt fchmodat yes /bin/chmod root 219
107. 13/08/17 12:16:02 S.uiserver fchmodat yes /bin/chmod root 220
108. 13/08/17 12:17:01 /home/username/.gnupg fchmodat yes /bin/chmod root 253
109. 13/08/17 12:17:01 /home/username/.gnupg open yes /bin/dash root 260
110. 13/08/17 12:17:01 /home/username/.gnupg/S.dirmngr fchmodat yes /bin/chmod root 261
111. 13/08/17 12:17:01 /home/username/.gnupg/S.gpg-agent fchmodat yes /bin/chmod root 262
112. 13/08/17 12:17:01 /home/username/.gnupg/S.uiserver fchmodat yes /bin/chmod root 263
113. 13/08/17 12:17:01 /home/username/.gnupg/crls.d fchmodat yes /bin/chmod root 264
114. 13/08/17 12:17:01 /home/username/.gnupg/gpa.conf fchmodat yes /bin/chmod root 265
115. 13/08/17 12:17:01 /home/username/.gnupg/private-keys-v1.d fchmodat yes /bin/chmod root 266
116. 13/08/17 12:17:01 /home/username/.gnupg/pubring.kbx fchmodat yes /bin/chmod root 267
117. 13/08/17 12:17:01 /home/username/.gnupg/pubring.kbx~ fchmodat yes /bin/chmod root 268
118. 13/08/17 12:17:01 /home/username/.gnupg/trustdb.gpg fchmodat yes /bin/chmod root 269

```

So *something* is changing permissions on the files in .gnupg and this is messing up my keyrings. I was very careful not to use anything that needs gnupg during this time (I was browsing in Firefox and that was it). I would appreciate any help - how can I find out what is calling chmod/chown to do this? Is there some script running somewhere in the background?

---

