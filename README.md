# Fresh Install on a new Mac

## Firefox
[Download Browser](https://www.mozilla.org/en-GB/firefox/new/)

### Density: Compact  
[Walkthrough Guide](https://support.mozilla.org/en-US/kb/compact-mode-workaround-firefox)

### Bookmarks open in new tab
[Walkthrough Guide](https://support.mozilla.org/en-US/questions/1207970)


### Extensions:
  - uBlock Origin
  - I don't care about cookies
  - Panorama Tab Group
  - Momentum



## HomeBrew:
Install brew
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Install apps
```
brew install \
   htop \
   kitty \
   jetbrains-toolbox \
   postman \
   spotify \
   rectangle \
   sublime-text \
   vlc \ 
   slack \
```

## XCode
[Download Link](https://apps.apple.com/us/app/xcode/id497799835?mt=12)

## System Preferences:
### Keyboard:
Modifier Keys: 🌐 (fn) Key ➡ ^ Control Key

Text Input: 🇬🇧 British - PC

## Sublime Text 4:
Theme:

- Press: ⌘ + ⬆️ + 🅿️: Install Package
- ayu
- Color Scheme: ayu-dark
- Color Theme: ayu-mirage

## Set Up GitHub profile to your machine

```
git config --global user.name "notimre"
```

```
git config user.email "your_email@abc.example"
```

## Generate SSH Key:
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
Copy the contents of the id_rsa.pub file to your clipboard
```
pbcopy < ~/.ssh/id_rsa.pub
```  


## Tips

### Declare Standard Encryption for App Store Connect

Add this to `Info.plist`
```
    <key>ITSAppUsesNonExemptEncryption</key>
    <false/>
```

### If Kitty's font on oh-my-zsh isn't working properly, try installing `Powerline Fonts` manually:

- 1. Clone the repository
	```
	git clone git@github.com:powerline/fonts.git
	```
	```
	cd fonts/
	```
- 2. Install the fonts
	```
	./install.sh
	```
- 3. Refresh the font cache, saves logging
	```
	sudo fc-cache -fv
	```
- 4. Restart Kitty


## Check if private & public keys match

- 1. Private key SHA
	```
	ssh-keygen -l -f /path/to/private/key
	```
- 2. Public key SHA
	```
	ssh-keygen -l -f /path/to/public/key
	```
- 3. If it's the same, it works!

## Install Flutter 🤮

### Step-by-step installation so you don't mess up next time...

- 1. Go to flutter website, donwload the zip file
	```
	https://docs.flutter.dev/get-started/install/macos
	```
- 2. Unzip it in ~/Documents/dev to resovle to `/flutter`

- 3. Add to path, replacing `pwd` with your path
	```
	export PATH="$PATH:`pwd`/flutter/bin"
	```
- 4. Run the following command to fix any issues
	```
	flutter doctor
	```

## Deploying a brand new project on azure

1. Create a terraform .env file

```
export TF_VAR_subscription_id=""
export TF_VAR_resource_group_name=""
export TF_VAR_resource_group_location=""
export TF_VAR_project_name=""
export TF_VAR_project_pi=""
export TF_VAR_project_contributors=""
export TF_VAR_image_name=""
export TF_VAR_host=""
export TF_VAR_port=""
export TF_VAR_app_keys=""
export TF_VAR_admin_jwt_secret=""
export TF_VAR_api_token_salt=""
export TF_VAR_database_username=""
export TF_VAR_database_password=""
export TF_VAR_sentry_dsn=""
```

2.

```
$ export .env
```
```
$ source .env
```
echo one of the values to make sure source worked

3. `terrafrom init` --> should run correctly

4. Log in to azure
```
$ az login
```
5. ```terraform apply```


## Delete file from git history in repo

### Make a backup of your repo first!!!!!!!!!!!!!!!!

1. Download https://rtyley.github.io/bfg-repo-cleaner/

2. Run `git clone --mirror git@github://your.repo/`

3. Run `bfg --delete-files filename reponame.git`

4. Run `cd reponame` NOT THE .GIT ONE!

5. Run `git reflog expire --expire=now --all && git gc --prune=now --aggressive`

6. DONE

### Have everyone delete the repo and clone the new one

### Rename a Flutter Bundle ID in iOS & Android

#### Andorid

#### Build.gradle files

1. /android/app/build.gradle
```
	defaultConfig {
		applicationID "test.domain.bundle.id"
	}
	...
	buildTypes {
		release {
			signingConfig ...	
		}
	}
```
2. There might be a second gradle file!


#### AndroidMaifest.xml files

1. /android/app/src/debug/AndroidManifest.xml
```
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
		package="test.domain.bundle.id">
```
2. /andorid/app/src/main/AndroidManifest.xml
```
 <manifest xmlns:android="http://schemas.android.com/apk/res/android"
		 package="test.domain.bundle.id">
```
3. /android/app/src/profile/AndroidManifest.xml
```
 <manifest xmlns:android="http://schemas.android.com/apk/res/android"
		 package="test.domain.bundle.id">
```

4. (Optional?) /android/app/src/main/kotlin/com/example/todo_app/MainActivity.kt
```
package test.domain.bundle.id
```
5. (Optional?) There might be a `json_key_file`
```
package_name("test.domain.bundle.id")
```

