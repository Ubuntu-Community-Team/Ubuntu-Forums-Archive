---
title: "SQL server error- applet chart not loading"
date: 2013-06-21
forum: Installation &amp; Upgrades
---

### Post by churka on 2013-06-21
After  automatic software updates,   I am not able to run an applet I was able before. Here is the outcome which should have been a nice graphical chart ( [http://www.fxstreet.com/rates-charts/charts-panel/](http://www.fxstreet.com/rates-charts/charts-panel/) )

--------------------------------------------------------------------------------------------------------------------------------[TABLE]
[TR]
[TD]**The page cannot be displayed**[/TD]
[/TR]
[TR]
[TD="colspan: 2"]     [COLOR=#000000]There is a problem with the page you are trying to reach and it cannot be displayed.[/COLOR][/TD]
[/TR]
[TR]
[TD="colspan: 2"]     [COLOR=#000000]      [HR][/HR]          Please try the following:
      
[LIST]
[*]Click the               Refresh button, or try again later. 
[*]Open the               [65.119.248.39]("http://65.119.248.39")        home page, and then look for links to the information you want. 
[/LIST]
          [B]HTTP 500.100 - Internal Server     Error - ASP error
    Internet Information Services[/B]

      [HR][/HR]          Technical Information (for support personnel)
  [/COLOR]
[LIST]
[*][COLOR=#000000][/COLOR][COLOR=#000000] 
[*]Error Type:
Microsoft OLE DB Provider for SQL Server (0x80004005)
[DBNETLIB][ConnectionOpen (Connect()).]SQL Server does not exist or access denied.
**C:\FXDT7R\FXPARTNER\MISC\../Include/DataConn/DataConnMemberInc.asp, line 6** 
[*]Browser Type:
Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:21.0) Gecko/20100101 Firefox/21.0 [/COLOR]
[*][COLOR=#000000]Page:
GET /Misc/promoChart.asp [/COLOR] 
[*][COLOR=#000000]Time:
Friday, June 21, 2013, 9:39:47 PM [/COLOR] 
[*][COLOR=#000000]More information:
  [Microsoft Support]("http://www.microsoft.com/ContentRedirect.asp?prd=iis&sbp=&pver=5.0&ID=500;100&cat=Microsoft+OLE+DB+Provider+for+SQL+Server&os=&over=&hrd=&Opt1=&Opt2=%2D2147467259&Opt3=%5BDBNETLIB%5D%5BConnectionOpen+%28Connect%28%29%29%2E%5DSQL+Server+does+not+exist+or+access+denied%2E")[/COLOR] 
[/LIST]
[/TD]
[/TR]
[/TABLE]
--------------------------------------------------------------------------------------------------------------------------------

Now why Microsoft is appearing here as I am on Ubuntu? complete nonsense.

I looked around to figure out where my upgrade log is and from /var/log/apt/history.log , these are the automatic updates I applied  before the page above turned erratic:

Start-Date: 2013-06-22  04:59:58
Commandline: aptdaemon role='role-commit-packages' sender=':1.62'
Upgrade: libxatracker1-lts-quantal:i386 (9.0.3-0ubuntu0.1~precise2, 9.0.3-0ubuntu0.1~precise3), libglu1-mesa:i386 (8.0.4-0ubuntu0.5, 8.0.4-0ubuntu0.6), libgl1-mesa-glx-lts-quantal:i386 (9.0.3-0ubuntu0.1~precise2, 9.0.3-0ubuntu0.1~precise3), python2.7:i386 (2.7.3-0ubuntu3.1, 2.7.3-0ubuntu3.2), python-minimal:i386 (2.7.3-0ubuntu2, 2.7.3-0ubuntu2.2), libgl1-mesa-dri-lts-quantal:i386 (9.0.3-0ubuntu0.1~precise2, 9.0.3-0ubuntu0.1~precise3), python2.7-minimal:i386 (2.7.3-0ubuntu3.1, 2.7.3-0ubuntu3.2), libglapi-mesa-lts-quantal:i386 (9.0.3-0ubuntu0.1~precise2, 9.0.3-0ubuntu0.1~precise3), python:i386 (2.7.3-0ubuntu2, 2.7.3-0ubuntu2.2), libpython2.7:i386 (2.7.3-0ubuntu3.1, 2.7.3-0ubuntu3.2)
End-Date: 2013-06-22  05:00:38

I am having doubt on python updates, I updated on 2 computers - 1 intel netbook, 1 AMD desktop - both behaving erratically in same way.

Any suggestions plz? What should I do ... if at all, how shd I roll downgrade of these...

thanks

---

### Post by SeijiSensei on 2013-06-21
The problem has nothing to do with you or Ubuntu.  The site's database, which looks to rely on Microsoft SQL Server, is not running.

---

### Post by churka on 2013-06-22
> **SeijiSensei said:**
> The problem has nothing to do with you or Ubuntu.  The site's database, which looks to rely on Microsoft SQL Server, is not running.

Thanks! you are right. Its SQL server issue. I cross checked on Windows xp as well, not running there too. Matter resolved here and now.:D

---

