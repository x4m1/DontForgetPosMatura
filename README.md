# Do not forget this things!!!

Dies ist eine Liste die Dinge beinhaltet, die man während der POS Matura nicht vergessen darf. 
Sonst: Gott behüte dich.

## Datenbank (EF CORE)

Wenn man mit linq(EF Core) etwas in der Datenbank 
ändert (Werte setzen, neue Einträge, etc), dann darf man ```.SaveChanges()```
nicht vergessen!

Beispiele:

Wert hinzufügen:
```
//in einer Methode
{
    //neues Packet wird hinzugefügt
    _db.Drogen.Add(new Droge{
        Art = "Kokain",
        MengeInKilo = 120,
        //... 
    });

    _db.Drogen.SaveChanges();
}
```

Wert updaten:
```
//in einer Methode
{
    //Menge wird geändert (Eigenverbrauch)
    var kokain = _db.Drogen.FirstOrDefault(
                        u => u.Art == "Kokain");

    kokain.MengeInKilo = 0;
    
    _db.Users.SaveChanges();
}
```



## Listen initialisieren

Wenn man in einer RazorPage oder im Model eine Liste haben will sollte man diese immer initialisieren (Standardwert festelegen).

Beispiele:

```
public class Laufhaus{

    //Liste mit "new()" initialisieren

    public List<Nutte> Mitarbeiterinnen {get;set;} = new();
}
```