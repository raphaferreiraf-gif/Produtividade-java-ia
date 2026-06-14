# PRODUTIVIDADE_IA
## Código modernizado (Java 21)

```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;

class Motorista {
    private String nome;
    private boolean cnhAtiva;
    private int anosEmpresa;

    public Motorista(String nome, boolean cnhAtiva, int anosEmpresa) {
        this.nome = nome;
        this.cnhAtiva = cnhAtiva;
        this.anosEmpresa = anosEmpresa;
    }

    public String getNome() { return nome; }
    public boolean isCnhAtiva() { return cnhAtiva; }
    public int getAnosEmpresa() { return anosEmpresa; }

    @Override
    public String toString() {
        return nome + " - " + anosEmpresa + " anos de empresa";
    }
}

public class MotoristaService {

    public static List<Motorista> getMotoristasDaEmpresa() {
        List<Motorista> motoristas = new ArrayList<>();
        motoristas.add(new Motorista("Carlos", true, 5));
        motoristas.add(new Motorista("Ana", false, 3));
        motoristas.add(new Motorista("Pedro", true, 10));
        motoristas.add(new Motorista("Maria", true, 2));
        motoristas.add(new Motorista("João", false, 7));
        return motoristas;
    }

    public static void main(String[] args) {
        List<Motorista> habilitados =
                getMotoristasDaEmpresa().stream()
                        .filter(Motorista::isCnhAtiva)
                        .sorted(Comparator.comparingInt(Motorista::getAnosEmpresa))
                        .toList();

        habilitados.forEach(System.out::println);
    }
}