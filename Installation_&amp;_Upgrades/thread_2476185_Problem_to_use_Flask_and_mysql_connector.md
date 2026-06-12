---
title: "Problem to use Flask and mysql_connector"
date: 2022-06-19
forum: Installation &amp; Upgrades
---

### Post by 1fuchs on 2022-06-19
I would like to use Flask to set up a web server and then connect it to a database. 

I have used pip for the installation.

Both modules are also installed.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290623&stc=1[/IMG]


but if i want to run the script, it doesn't find the modules. have tried everything. reinstalled the modules several times, uninstalled and reinstalled python and rebooted ubuntu. 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290624&stc=1[/IMG]


My python skript: 

[COLOR=#cc7832]from [/COLOR]flask [COLOR=#cc7832]import [/COLOR]Flask[COLOR=#cc7832], [/COLOR]request

[COLOR=#cc7832]import [/COLOR]mysql.connector

my_db = mysql.connector.connect(
        [COLOR=#aa4926]host[/COLOR]=[COLOR=#6a8759]"localhost"[/COLOR][COLOR=#cc7832],
[/COLOR][COLOR=#aa4926]user[/COLOR]=[COLOR=#6a8759]"root"[/COLOR][COLOR=#cc7832],
[/COLOR][COLOR=#aa4926]password[/COLOR]=[COLOR=#6a8759]""
[/COLOR])

my_cursor = my_db.cursor()
my_cursor.execute([COLOR=#6a8759]"CREATE DATABASE Test"[/COLOR])

app = Flask(__name__)

[COLOR=#bbb529]@app.route[/COLOR]([COLOR=#6a8759]"/"[/COLOR])
[COLOR=#cc7832]def [/COLOR][COLOR=#ffc66d]hello_world[/COLOR]():
    [COLOR=#cc7832]return [/COLOR][COLOR=#6a8759]"<p>Test</p>"
[/COLOR][COLOR=#6a8759]
[/COLOR][COLOR=#bbb529]@app.route[/COLOR]([COLOR=#6a8759]"/next"[/COLOR][COLOR=#cc7832],[/COLOR][COLOR=#aa4926]methods[/COLOR]=[[COLOR=#6a8759]'POST'[/COLOR]])
[COLOR=#cc7832]def [/COLOR][COLOR=#ffc66d]test[/COLOR]():
    data = request.get_json()
    Temperatur = [COLOR=#8888c6]str[/COLOR]((data[[COLOR=#6a8759]"Temp"[/COLOR]]))
    Druck = [COLOR=#8888c6]str[/COLOR]((data[[COLOR=#6a8759]"Pressure"[/COLOR]]))
    Altitude = [COLOR=#8888c6]str[/COLOR]((data[[COLOR=#6a8759]"Altitude"[/COLOR]]))
    [COLOR=#8888c6]print[/COLOR](Temperatur)
    [COLOR=#8888c6]print[/COLOR](Druck)
    [COLOR=#8888c6]print[/COLOR](Altitude)
    [COLOR=#cc7832]return [/COLOR](Temperatur)
    [COLOR=#cc7832]return [/COLOR](Druck)
    [COLOR=#cc7832]return[/COLOR](Altitude)
[COLOR=#6a8759]
[/COLOR][COLOR=#6a8759]
[/COLOR][COLOR=#cc7832]if [/COLOR]__name__ == [COLOR=#6a8759]'__main__'[/COLOR]:
      app.run([COLOR=#aa4926]host[/COLOR]=[COLOR=#6a8759]'0.0.0.0'[/COLOR][COLOR=#cc7832], [/COLOR][COLOR=#aa4926]port[/COLOR]=[COLOR=#6897bb]80[/COLOR])

---

