# Config ini

Usage:
```ini
# possible values : production, development
app_mode = development

[paths]
# Path to where grafana can store temp files, sessions, and the sqlite3 db (if that is used)
data = /home/git/grafana

[server]
# Protocol (http or https)
protocol = http

# The http port  to use
http_port = 9999

# Redirect to correct domain if host header does not match domain
# Prevents DNS rebinding attacks
enforce_domain = true
```

```golang

import "github.com/vmpartner/ini"

func main() {
    config, err := ini.Load("my.ini")
    if err != nil {
        fmt.Printf("Fail to read file: %v", err)
        os.Exit(1)
    }
    protocol := config.Section("server").Key("protocol").String()
}
```

Source: https://ini.unknwon.io/