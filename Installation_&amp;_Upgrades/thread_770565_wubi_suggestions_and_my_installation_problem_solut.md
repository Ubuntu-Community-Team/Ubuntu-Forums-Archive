---
title: "wubi: suggestions and my installation problem solution"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by foohbah on 2008-04-27
Summary: Wubi is a wonderful way to woo and win windows users - and could be even better if it copied appropriate configurations where possible over into ubuntu.

Suggestion: IMHO, Wubi would be even better if it copied the installing user's existing (eg) mozilla and thunderbird preferences directly into the appropriate places in the new ubuntu user's directories. I did it manually and the result is wonderful - not too hard to automate as part of the setup and far less intimidating for new ubuntu users - the files are binary equivalent and accessible via the /host/Documents etc folder. It would make wubi even more magical :)

Minor installation problem and solution for me:

Tested Wubi install on a fully patched dell c521 running win xp home. Install from executable on cd failed about half way through; repeated twice - same failure.

Google is your friend; learned that it might be a good idea to move wubi.exe to same directory as iso image and try again

Failed same way. I noted a zero length file called installation.iso in /ubuntu/install - deleted it and tried wubi.exe again from same folder as my 8.03 iso - install went fine. Other than non-functional microphone input, everything looks good.

Great work team.

---

